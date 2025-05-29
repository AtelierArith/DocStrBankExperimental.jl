```
rrrMC(X::AbstractGraph, β::Real, iters::Integer; keywords...)
```

Same as [`standardMC`](@ref), but uses the reduced-rejection-rate method. Each iteration takes more time, but has a higher chance of being accepted, so fewer iterations overall should be needed normally. Whether this trade-off is convenient depends on the parameters and the details of the model. This function has specialized versions for [`DiscrGraph`](@ref) and [`DoubleGraph`](@ref) models.

The return values and the keyword arguments are the same as [`standardMC`](@ref), see the usage examples for that function.
