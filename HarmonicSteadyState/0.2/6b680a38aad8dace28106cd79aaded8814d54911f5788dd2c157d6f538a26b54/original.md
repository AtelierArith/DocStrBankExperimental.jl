```julia
get_class(
    soln::HarmonicSteadyState.Result,
    class::String
) -> Vector

```

Returns an array of booleans classifying each branch in the solutions in `res` according to `class`.
