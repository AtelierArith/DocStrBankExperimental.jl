```
get_session_id(req::HTTP.Request, res::HTTP.Response)::Union{String, Nothing}
```

Get the session id from a HTTP.Request or HTTP.Response object. First will try to get the session id from the HTTP.Request object. If it does not exist, it will try to get it from the HTTP.Response object.

# Arguments

  * `req`: the HTTP.Request object.
  * `res`: the HTTP.Response object.

# Return

The function returns the session id if it exists, otherwise it returns nothing.
