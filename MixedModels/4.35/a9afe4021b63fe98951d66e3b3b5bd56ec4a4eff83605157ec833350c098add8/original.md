```
refit!(m::GeneralizedLinearMixedModel[, y::Vector];
       fast::Bool = (length(m.θ) == length(m.optsum.final)),
       nAGQ::Integer = m.optsum.nAGQ,
       kwargs...)
```

Refit the model `m` after installing response `y`.

If `y` is omitted the current response vector is used.

If not specified, the `fast` and `nAGQ` options from the previous fit are used. `kwargs` are the same as [`fit!`](@ref)
