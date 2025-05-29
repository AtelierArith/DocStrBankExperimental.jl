```
get_session_storage(session_id::String)::Union{Session, Nothing}
```

Get a session from the session storage for a session id.

# Arguments

  * `session_id`: the session id.

# Return

The function returns the session if it exists, otherwise it returns nothing.
