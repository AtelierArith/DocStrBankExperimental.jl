```
get_session(
    req::HTTP.Request,
    res::HTTP.Response
)::Union{Session, Nothing}
```

Get a session from the session storage for a HTTP.Request and HTTP.Response object. If the session does not exist, it is created.

# Arguments

  * `req`: the HTTP.Request object.
  * `res`: the HTTP.Response object.

# Return

The function returns the session if it exists, otherwise it returns the newly created.
