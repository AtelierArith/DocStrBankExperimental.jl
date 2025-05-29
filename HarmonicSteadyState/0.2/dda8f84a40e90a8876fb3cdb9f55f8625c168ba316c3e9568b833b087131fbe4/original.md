```julia
filter_result!(
    res::HarmonicSteadyState.Result,
    class::String
)

```

Removes all solution branches from `res` where NONE of the solution falls into `class`. Typically used to filter out unphysical solutions to prevent huge file sizes.
