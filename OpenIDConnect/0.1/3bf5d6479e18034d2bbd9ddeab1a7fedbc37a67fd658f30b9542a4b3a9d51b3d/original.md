Given the params from the redirected response from the authentication request, extract the authorization code. See sections 3.1.2.5 and 3.1.2.6 of https://openid.net/specs/openid-connect-core-1_0.html.

Returns the authorization code on success. Returns one of APIError or AuthServerError on failure.
