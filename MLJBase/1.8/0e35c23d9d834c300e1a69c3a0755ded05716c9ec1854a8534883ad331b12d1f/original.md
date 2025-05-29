```
fitted_params(signature; supplement=true)
```

**Private method.**

Generate a fitted*params for the learning network associated with `signature`, including the supplementary fitted*params.

Suppress calling of the fitted_params nodes of `signature`, and excluded their contribution to the output, by specifying `supplement=false`.

See also [`MLJBase.fitted_params_supplement`](@ref).

See also [`MLJBase.Signature`](@ref).
