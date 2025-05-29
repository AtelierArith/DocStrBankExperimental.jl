```
linkjs(session::Session, a::Observable, b::Observable)
```

for an open session, link a and b on the javascript side. This will also Link the observables in Julia, but only as long as the session is active.
