```
fit(Mod::Type{<:StatisticalModel}, f::FormulaTerm, data, args...;
    contrasts::Dict{Symbol}, kwargs...)
```

Convert tabular data into a numeric response vector and predictor matrix using the formula `f`, and then `fit` the specified model type, wrapping the result in a [`TableRegressionModel`](@ref) or [`TableStatisticalModel`](@ref) (as appropriate).

This is intended as a backstop for modeling packages that implement model types that are subtypes of `StatsBase.StatisticalModel` but do not explicitly support the full StatsModels terms-based interface.  Currently this works by creating a [`ModelFrame`](@ref) from the formula and data, and then converting this to a [`ModelMatrix`](@ref), but this is an internal implementation detail which may change in the near future.
