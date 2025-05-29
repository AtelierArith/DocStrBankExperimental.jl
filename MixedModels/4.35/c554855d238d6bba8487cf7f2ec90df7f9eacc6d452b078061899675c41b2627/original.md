```
refit!(m::LinearMixedModel[, y::Vector]; REML=m.optsum.REML, kwargs...)
```

Refit the model `m` after installing response `y`.

If `y` is omitted the current response vector is used. `kwargs` are the same as [`fit!`](@ref).
