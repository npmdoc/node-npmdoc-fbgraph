# api documentation for  [fbgraph (v1.4.1)](https://github.com/criso/fbgraph#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-fbgraph.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-fbgraph) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-fbgraph.svg)](https://travis-ci.org/npmdoc/node-npmdoc-fbgraph)
#### Facebook Graph API client

[![NPM](https://nodei.co/npm/fbgraph.png?downloads=true)](https://www.npmjs.com/package/fbgraph)

[![apidoc](https://npmdoc.github.io/node-npmdoc-fbgraph/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-fbgraph_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-fbgraph/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-fbgraph/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-fbgraph/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Cristiano Oliveira",
        "email": "ocean.cris@gmail.com"
    },
    "bugs": {
        "url": "https://github.com/criso/fbgraph/issues"
    },
    "dependencies": {
        "qs": "^1.2.2",
        "request": "^2.79.0"
    },
    "description": "Facebook Graph API client",
    "devDependencies": {
        "vows": "^0.7.0"
    },
    "directories": {},
    "dist": {
        "shasum": "b2aa380f9ef7da302978d0749fad699fb974c104",
        "tarball": "https://registry.npmjs.org/fbgraph/-/fbgraph-1.4.1.tgz"
    },
    "engines": {
        "node": ">= 0.4.1"
    },
    "gitHead": "894fa3153d745ac0de5d37b5ca905c98f98e8f68",
    "homepage": "https://github.com/criso/fbgraph#readme",
    "keywords": [
        "facebook",
        "api",
        "graph"
    ],
    "license": "MIT",
    "main": "index",
    "maintainers": [
        {
            "name": "criso",
            "email": "ocean.cris@gmail.com"
        }
    ],
    "name": "fbgraph",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git://github.com/criso/fbgraph.git"
    },
    "scripts": {},
    "version": "1.4.1"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module fbgraph](#apidoc.module.fbgraph)
1.  [function <span class="apidocSignatureSpan">fbgraph.</span>authorize (params, callback)](#apidoc.element.fbgraph.authorize)
1.  [function <span class="apidocSignatureSpan">fbgraph.</span>batch (reqs, additionalData, callback)](#apidoc.element.fbgraph.batch)
1.  [function <span class="apidocSignatureSpan">fbgraph.</span>del (url, postData, callback)](#apidoc.element.fbgraph.del)
1.  [function <span class="apidocSignatureSpan">fbgraph.</span>extendAccessToken (params, callback)](#apidoc.element.fbgraph.extendAccessToken)
1.  [function <span class="apidocSignatureSpan">fbgraph.</span>fql (query, params, callback)](#apidoc.element.fbgraph.fql)
1.  [function <span class="apidocSignatureSpan">fbgraph.</span>get (url, params, callback)](#apidoc.element.fbgraph.get)
1.  [function <span class="apidocSignatureSpan">fbgraph.</span>getAccessToken ()](#apidoc.element.fbgraph.getAccessToken)
1.  [function <span class="apidocSignatureSpan">fbgraph.</span>getAppSecret ()](#apidoc.element.fbgraph.getAppSecret)
1.  [function <span class="apidocSignatureSpan">fbgraph.</span>getGraphUrl ()](#apidoc.element.fbgraph.getGraphUrl)
1.  [function <span class="apidocSignatureSpan">fbgraph.</span>getOauthUrl (params, opts)](#apidoc.element.fbgraph.getOauthUrl)
1.  [function <span class="apidocSignatureSpan">fbgraph.</span>getOptions ()](#apidoc.element.fbgraph.getOptions)
1.  [function <span class="apidocSignatureSpan">fbgraph.</span>post (url, postData, callback)](#apidoc.element.fbgraph.post)
1.  [function <span class="apidocSignatureSpan">fbgraph.</span>search (options, callback)](#apidoc.element.fbgraph.search)
1.  [function <span class="apidocSignatureSpan">fbgraph.</span>setAccessToken (token)](#apidoc.element.fbgraph.setAccessToken)
1.  [function <span class="apidocSignatureSpan">fbgraph.</span>setAppSecret (token)](#apidoc.element.fbgraph.setAppSecret)
1.  [function <span class="apidocSignatureSpan">fbgraph.</span>setGraphUrl (url)](#apidoc.element.fbgraph.setGraphUrl)
1.  [function <span class="apidocSignatureSpan">fbgraph.</span>setOptions (options)](#apidoc.element.fbgraph.setOptions)
1.  [function <span class="apidocSignatureSpan">fbgraph.</span>setVersion (version)](#apidoc.element.fbgraph.setVersion)
1.  string <span class="apidocSignatureSpan">fbgraph.</span>version



# <a name="apidoc.module.fbgraph"></a>[module fbgraph](#apidoc.module.fbgraph)

#### <a name="apidoc.element.fbgraph.authorize"></a>[function <span class="apidocSignatureSpan">fbgraph.</span>authorize (params, callback)](#apidoc.element.fbgraph.authorize)
- description and source-code
```javascript
authorize = function (params, callback) {
  var self = this;

  return this.get("/oauth/access_token", params, function(err, res) {
    if (!err) self.setAccessToken(res.access_token);

    callback(err, res);
  });
}
```
- example usage
```shell
...
});

// shows dialog
res.redirect(authUrl);

// after user click, auth 'code' will be set
// we'll send that and get the access token
graph.authorize({
    "client_id":      conf.client_id
  , "redirect_uri":   conf.redirect_uri
  , "client_secret":  conf.client_secret
  , "code":           req.query.code
}, function (err, facebookRes) {
  res.redirect('/loggedIn');
});
...
```

#### <a name="apidoc.element.fbgraph.batch"></a>[function <span class="apidocSignatureSpan">fbgraph.</span>batch (reqs, additionalData, callback)](#apidoc.element.fbgraph.batch)
- description and source-code
```javascript
batch = function (reqs, additionalData, callback) {
  if (!(reqs instanceof Array)) {
    return callback({ message: 'Graph api batch requests must be an array' }, null);
  }

  if (typeof additionalData === 'function') {
    callback = additionalData;
    additionalData = {};
  }

  return new Graph('POST', '', extend({}, {
    access_token: accessToken,
    batch: JSON.stringify(reqs)
  }, additionalData), callback);
}
```
- example usage
```shell
...
'''

## Performing a batch request

[Batching](https://developers.facebook.com/docs/graph-api/making-multiple-requests) allows you to pass instructions for several
operations in a single HTTP request.

'''js
graph.batch([
{
  method: "GET",
  relative_url: "me" // Get the current user's profile information
},
{
  method: "GET",
  relative_url: "me/friends?limit=50" // Get the first 50 friends of the current user
...
```

#### <a name="apidoc.element.fbgraph.del"></a>[function <span class="apidocSignatureSpan">fbgraph.</span>del (url, postData, callback)](#apidoc.element.fbgraph.del)
- description and source-code
```javascript
del = function (url, postData, callback) {
  if (!url.match(/[?|&]method=delete/i)) {
    url += ~url.indexOf('?') ? '&' : '?';
    url += 'method=delete';
  }

  if (typeof postData === 'function') {
    callback = postData;
    postData = url.indexOf('access_token') !== -1 ? {} : {access_token: accessToken};
  }

  return this.post(url, postData, callback);
}
```
- example usage
```shell
...

## Delete a Graph object

To delete a graph object, provide an 'object id' and the
response will return '{data: true}' or '{data:false}'

'''js
graph.del(postID, function(err, res) {
  console.log(res); // {data:true}/{data:false}
});
'''

## Performing a batch request

[Batching](https://developers.facebook.com/docs/graph-api/making-multiple-requests) allows you to pass instructions for several
operations in a single HTTP request.
...
```

#### <a name="apidoc.element.fbgraph.extendAccessToken"></a>[function <span class="apidocSignatureSpan">fbgraph.</span>extendAccessToken (params, callback)](#apidoc.element.fbgraph.extendAccessToken)
- description and source-code
```javascript
extendAccessToken = function (params, callback) {
    var self = this;

    params.grant_type        = 'fb_exchange_token';
    params.fb_exchange_token = params.access_token ? params.access_token : this.getAccessToken();

    return this.get("/oauth/access_token", params, function(err, res) {
      if (!err && !params.access_token) {
        self.setAccessToken(res.access_token);
      }

      callback(err, res);
    });
}
```
- example usage
```shell
...

## Extending access token expiration time

If you want to [extend the expiration time](http://developers.facebook.com/docs/facebook-login/access-tokens/#extending) of your
 short-living access token, you may use 'extendAccessToken' method as it is shown below:

'''js
// extending static access token
graph.extendAccessToken({
    "client_id":      conf.client_id
  , "client_secret":  conf.client_secret
}, function (err, facebookRes) {
   console.log(facebookRes);
});

// extending specific access token
...
```

#### <a name="apidoc.element.fbgraph.fql"></a>[function <span class="apidocSignatureSpan">fbgraph.</span>fql (query, params, callback)](#apidoc.element.fbgraph.fql)
- description and source-code
```javascript
fql = function (query, params, callback) {
  if (typeof query !== 'string') query = JSON.stringify(query);

  var url = '/fql?q=' + encodeURIComponent(query);

  if (typeof params === 'function') {
    callback = params;
    params = null;
    return this.get(url, callback);
  } else {
    return this.get(url, params, callback);
  }
}
```
- example usage
```shell
...
## Performing a FQL query

A single FQL query is done by sending a query as a string

'''js
var query = "SELECT name FROM user WHERE uid = me()";

graph.fql(query, function(err, res) {
  console.log(res); // { data: [ { name: 'Ricky Bobby' } ] }
});
'''

You can specify additional options by adding a JSON object
'''js
var query = "SELECT name FROM user WHERE uid = me()";
...
```

#### <a name="apidoc.element.fbgraph.get"></a>[function <span class="apidocSignatureSpan">fbgraph.</span>get (url, params, callback)](#apidoc.element.fbgraph.get)
- description and source-code
```javascript
get = function (url, params, callback) {
  if (typeof params === 'function') {
    callback = params;
    params   = null;
  }

  if (typeof url !== 'string') {
    return callback({ message: 'Graph api url must be a string' }, null);
  }

  if (params)  {
    url += ~url.indexOf('?') ? '&' : '?';
    url += qs.stringify(params);
  }

  return new Graph('GET', url, callback);
}
```
- example usage
```shell
...
    timeout:  3000
  , pool:     { maxSockets:  Infinity }
  , headers:  { connection:  "keep-alive" }
};

graph
  .setOptions(options)
  .get("zuck", function(err, res) {
    console.log(res); // { id: '4', name: 'Mark Zuckerberg'... }
  });
'''

Possible options can be found on the [request github page](https://github.com/mikeal/request)

'followRedirect' cannot be overriden and has a default value of 'false'
...
```

#### <a name="apidoc.element.fbgraph.getAccessToken"></a>[function <span class="apidocSignatureSpan">fbgraph.</span>getAccessToken ()](#apidoc.element.fbgraph.getAccessToken)
- description and source-code
```javascript
getAccessToken = function () {
  return accessToken;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.fbgraph.getAppSecret"></a>[function <span class="apidocSignatureSpan">fbgraph.</span>getAppSecret ()](#apidoc.element.fbgraph.getAppSecret)
- description and source-code
```javascript
getAppSecret = function () {
  return appSecret;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.fbgraph.getGraphUrl"></a>[function <span class="apidocSignatureSpan">fbgraph.</span>getGraphUrl ()](#apidoc.element.fbgraph.getGraphUrl)
- description and source-code
```javascript
getGraphUrl = function () {
  return graphUrl;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.fbgraph.getOauthUrl"></a>[function <span class="apidocSignatureSpan">fbgraph.</span>getOauthUrl (params, opts)](#apidoc.element.fbgraph.getOauthUrl)
- description and source-code
```javascript
getOauthUrl = function (params, opts) {
  var url = (opts && opts.mobile) ? oauthDialogUrlMobile : oauthDialogUrl;
  return url + qs.stringify(params);
}
```
- example usage
```shell
...


This is how you would get authenticated using only the 'fbgraph' module.
More details below on the __express app__ section

'''js
// get authorization url
var authUrl = graph.getOauthUrl({
    "client_id":     conf.client_id
  , "redirect_uri":  conf.redirect_uri
});

// shows dialog
res.redirect(authUrl);
...
```

#### <a name="apidoc.element.fbgraph.getOptions"></a>[function <span class="apidocSignatureSpan">fbgraph.</span>getOptions ()](#apidoc.element.fbgraph.getOptions)
- description and source-code
```javascript
getOptions = function () {
  return requestOptions;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.fbgraph.post"></a>[function <span class="apidocSignatureSpan">fbgraph.</span>post (url, postData, callback)](#apidoc.element.fbgraph.post)
- description and source-code
```javascript
post = function (url, postData, callback) {
  if (typeof url !== 'string') {
    return callback({ message: 'Graph api url must be a string' }, null);
  }

  if (typeof postData === 'function') {
    callback = postData;
    postData = url.indexOf('access_token') !== -1 ? {} : {access_token: accessToken};
  }

  return new Graph('POST', url, postData, callback);
}
```
- example usage
```shell
...
'''js
    graph.setAccessToken(access_token);
'''

### To use a specific access token for a particular request
'''js
    // pass it in as part of the url
    graph.post(userId + "/feed?access_token=007", wallPost, function(err, res) {
        // returns the post id
        console.log(res); // { id: xxxxx}
    });

'''
...
```

#### <a name="apidoc.element.fbgraph.search"></a>[function <span class="apidocSignatureSpan">fbgraph.</span>search (options, callback)](#apidoc.element.fbgraph.search)
- description and source-code
```javascript
search = function (options, callback) {
  options = options || {};
  var url = '/search?' + qs.stringify(options);
  return this.get(url, callback);
}
```
- example usage
```shell
...

'''js
var searchOptions = {
    q:     "brogramming"
  , type:  "post"
};

graph.search(searchOptions, function(err, res) {
  console.log(res); // {data: [{id: xxx, from: ...}, {id: xxx, from: ...}]}
});
'''

## Publish data to the Graph Api
All publish requests will require an 'access token'
...
```

#### <a name="apidoc.element.fbgraph.setAccessToken"></a>[function <span class="apidocSignatureSpan">fbgraph.</span>setAccessToken (token)](#apidoc.element.fbgraph.setAccessToken)
- description and source-code
```javascript
setAccessToken = function (token) {
  accessToken = token;
  return this;
}
```
- example usage
```shell
...
If you get an accesstoken via some other Oauth module like [everyauth](https://github.com/bnoguchi/everyauth) ,
[connect-auth](https://github.com/ciaranj/connect-auth) or [node-oauth](https://github.com/ciaranj/node-oauth) you can just set
the access token directly. Most 'get' calls, and pretty much all 'post' calls will require an 'access_token'


### Static access token (used on all calls)
'''js
graph.setAccessToken(access_token);
'''

### To use a specific access token for a particular request
'''js
// pass it in as part of the url
graph.post(userId + "/feed?access_token=007", wallPost, function(err, res) {
    // returns the post id
...
```

#### <a name="apidoc.element.fbgraph.setAppSecret"></a>[function <span class="apidocSignatureSpan">fbgraph.</span>setAppSecret (token)](#apidoc.element.fbgraph.setAppSecret)
- description and source-code
```javascript
setAppSecret = function (token) {
  appSecret = token;
  return this;
}
```
- example usage
```shell
...
    });
'''

### Securing API calls

Facebook [recommends](https://developers.facebook.com/docs/reference/api/securing-graph-api/) adding the
'appsecret_proof' parameter to all API calls to verify that the access tokens are coming from a valid app.
You can make this happen automatically by calling 'graph.setAppSecret(app_secret)', which will be used on
all calls to generate the 'appsecret_proof' hash that is sent to Facebook.  Make sure you also set the
access token for the user via 'graph.setAccessToken'.

## Extending access token expiration time

If you want to [extend the expiration time](http://developers.facebook.com/docs/facebook-login/access-tokens/#extending) of your
 short-living access token, you may use 'extendAccessToken' method as it is shown below:
...
```

#### <a name="apidoc.element.fbgraph.setGraphUrl"></a>[function <span class="apidocSignatureSpan">fbgraph.</span>setGraphUrl (url)](#apidoc.element.fbgraph.setGraphUrl)
- description and source-code
```javascript
setGraphUrl = function (url) {
  graphUrl = url;
  return this;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.fbgraph.setOptions"></a>[function <span class="apidocSignatureSpan">fbgraph.</span>setOptions (options)](#apidoc.element.fbgraph.setOptions)
- description and source-code
```javascript
setOptions = function (options) {
  if (typeof options === 'object')  requestOptions = options;

  return this;
}
```
- example usage
```shell
...
var options = {
    timeout:  3000
  , pool:     { maxSockets:  Infinity }
  , headers:  { connection:  "keep-alive" }
};

graph
  .setOptions(options)
  .get("zuck", function(err, res) {
    console.log(res); // { id: '4', name: 'Mark Zuckerberg'... }
  });
'''

Possible options can be found on the [request github page](https://github.com/mikeal/request)
...
```

#### <a name="apidoc.element.fbgraph.setVersion"></a>[function <span class="apidocSignatureSpan">fbgraph.</span>setVersion (version)](#apidoc.element.fbgraph.setVersion)
- description and source-code
```javascript
setVersion = function (version) {
  // set version
  graphVersion = version;

  // update auth urls
  oauthDialogUrl       = "http://www.facebook.com/v"+version+"/dialog/oauth?"; // oldest version for auth
  oauthDialogUrlMobile = "http://m.facebook.com/v"+version+"/dialog/oauth?";   // oldest version for auth

  return this;
}
```
- example usage
```shell
...
  }
});
'''

## Setting the version of the Graph Api

'''js
graph.setVersion("2.8");
'''

See [Facebook API changelog](https://developers.facebook.com/docs/apps/changelog) for available versions.

## Read data from the Graph Api

'''js
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
