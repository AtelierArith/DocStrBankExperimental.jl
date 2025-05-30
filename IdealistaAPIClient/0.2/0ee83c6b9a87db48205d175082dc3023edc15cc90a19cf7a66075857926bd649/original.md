```
get_token()
```

Return Idealista Search API parsed response for token request

# Notes

APIKEY and SECRET must be defined as environmental variables. Generated tokens get cached in tempdir, and any new calls to the get_token function before the expiration date will return the cached value

# Examples

```julia
julia>get_token()
[ Info: Getting new access token
Dict{String, Any} with 5 entries:
  "access_token" => "token_value"
  "token_type"   => "bearer"
  "scope"        => "read"
  "expires_in"   => DateTime("2022-08-14T03:07:24.573")
  "jti"          => "jti_value"

```
