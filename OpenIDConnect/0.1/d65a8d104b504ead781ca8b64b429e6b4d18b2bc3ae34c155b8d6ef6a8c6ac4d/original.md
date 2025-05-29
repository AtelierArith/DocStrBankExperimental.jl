Token Request. Given the authorization code obtained, invoke the token end point and obtain an id*token, access*token, refresh*token. See section 3.1.3.1 of https://openid.net/specs/openid-connect-core-1*0.html.

Returns a JSON object containing tokens on success. Returns a AuthServerError or APIError object on failure.
