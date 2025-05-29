```
state(A::Union{Jet,Jop,JopAdjoint}[, key])
```

If `key::Symbol` is specified, then return the state corresponding to `key`. Otherwise, return the state of A as a `NamedTuple`.
