```
without_authentication(f::Function, session)
without_authentication(f::Function, params::Dict{Symbol,Any})
```

Invokes `f` if there is no user authenticated on the current session.
