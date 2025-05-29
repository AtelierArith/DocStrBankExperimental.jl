```
with_authentication(f::Function, fallback::Function, session)
with_authentication(f::Function, fallback::Function, params::Dict{Symbol,Any})
```

Invokes `f` only if a user is currently authenticated on the session, `fallback` is invoked otherwise.
