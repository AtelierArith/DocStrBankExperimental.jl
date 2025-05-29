```
get_cookie(
    payload::Union{HTTP.Request, HTTP.Response},
    name::String
)::Union{HTTP.Cookie, Nothing}
```

Get a cookie from a HTTP.Request or HTTP.Response object.

# Arguments

  * `payload`: the HTTP.Request or HTTP.Response object.
  * `name`: the name of the cookie.

# Return

The function returns the cookie if it exists, otherwise it returns nothing.
