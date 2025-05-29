```
session_exists(payload::Union{HTTP.Request, HTTP.Response})::Bool
```

Check if a session exists for a HTTP.Request or HTTP.Response object.

# Arguments

  * `payload`: the HTTP.Request or HTTP.Response object.

# Return

The function returns true if the session exists, otherwise it returns false.
