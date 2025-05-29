```
WindowVect{V} <: AbstractWindowShape
```

A user-specified window vector, constructed via `WindowVect(v::V)`, where `v` is a `AbstractVector`. Caution: `length(v)` must be appropriate for the padded sinogram size.
