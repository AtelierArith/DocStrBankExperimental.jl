Token Refresh. Given the refresh code obtained, invoke the token end point and obtain new tokens. See section 12 of https://openid.net/specs/openid-connect-core-1_0.html.

Returns a JSON object containing tokens on success. Returns a AuthServerError or APIError object on failure.
