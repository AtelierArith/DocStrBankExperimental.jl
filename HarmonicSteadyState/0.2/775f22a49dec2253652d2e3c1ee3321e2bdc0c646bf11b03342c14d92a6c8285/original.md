```julia
get_class(
    res::HarmonicSteadyState.Result,
    branch::Int64,
    class::String
) -> Any

```

Returns an array of booleans classifying `branch` in the solutions in `res` according to `class`.
