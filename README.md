# connect_facebook

Facebook session support for [Connect](http://senchalabs.github.com/connect/).

*connect\_facebook* enables you to build web sites that use [Facebook authentication](https://developers.facebook.com/docs/reference/javascript/FB.login/) both on the front-end (HTML/JS) and the back-end (server-side), allowing for a smooth user experience.

This middleware reads and cryptographically verifies the session, making it accessible from `req.fb_session` -- an object if authorized and valid, otherwise the request has no valid Facebook user session. The `req.fb_session` object is the same as returned by the client-side `FB.getLoginStatus`, `auth.sessionChange` event, etc.


## Example

server.mv

    import connect, connect_facebook
    connect()
      .use(connect_facebook('YOUR_FACEBOOK_APP_ID', 'YOUR_FACEBOOK_APP_SECRET'))
      .use(^(req, res, next) {
        res.end(req.fb_session ? 'Logged in' : 'Not logged in')
      })
      .listen 3000

See `example/` for a complete demo including client-side code.


## MIT license

Copyright (c) 2011 Rasmus Andersson <http://rsms.me/>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
