```
authorize(refresh_token::AbstractString)
authorize(emailaddress::AbstractString, password::AbstractString)
```

Authorize by the refresh token `refresh_token`, or the combination of email address `emailaddress` and password `password`. Return `true` after the authorization.

The details of this API are [here](https://jpx.gitbook.io/j-quants-api-en/api-reference/refreshtoken) and [here](https://jpx.gitbook.io/j-quants-api-en/api-reference/refresh).

This package temporally holds your ID Token and Refresh Token as the package-internal variables. Once authorized, reauthorization is not required until that the process of Julia exits or the tokens expires. You can check your tokens using `JQuants.check_refresh_token()` and `JQuants.check_id_token()`.

# Examples

```jldoctest
julia> reftoken = [YOUR REFRESH TOKEN];

julia> authorize(reftoken)
true
```

```jldoctest
julia> email, pass = [YOUR EMAIL ADDRESS], [YOUR PASSWORD]

julia> authorize(email, pass)
true
```
