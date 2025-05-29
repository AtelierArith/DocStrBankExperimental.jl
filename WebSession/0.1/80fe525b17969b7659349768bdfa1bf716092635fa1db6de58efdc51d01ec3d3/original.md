```
start_session(req::HTTP.Request, res::HTTP.Response)::Session
```

Starts a session to an HTTP.Request and HTTP.Response object.   Checks if the session already exists and if it does, returns it.   The cookie is set in the response. The session is added to the session store.  

# Arguments

  * `req`: the HTTP.Request object.
  * `res`: the HTTP.Response object.

# Return

The function returns the new session or an existing session.
