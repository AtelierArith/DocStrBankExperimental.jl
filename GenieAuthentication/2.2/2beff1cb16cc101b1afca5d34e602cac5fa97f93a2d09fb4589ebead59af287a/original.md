```
logout(session) :: Sessions.Session
logout(params::Dict{Symbol,Any}) :: Sessions.Session
```

Deletes the id of the user object from the session, effectively logging the user off.
