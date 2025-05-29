```
function loo(args...; kwargs...) -> PsisLoo
```

Compute an approximate leave-one-out cross-validation score.

Currently, this function only serves to call `psis_loo`, but this could change in the future. The default methods or return type may change without warning, so we recommend using `psis_loo` instead if reproducibility is required.

See also: [`psis_loo`](@ref), [`PsisLoo`](@ref).
