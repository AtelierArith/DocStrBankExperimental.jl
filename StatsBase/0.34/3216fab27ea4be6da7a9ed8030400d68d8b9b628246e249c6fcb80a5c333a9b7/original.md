```
mean_and_var(x, [w::AbstractWeights], [dim]; corrected=true) -> (mean, var)
```

Return the mean and variance of collection `x`. If `x` is an `AbstractArray`, `dim` can be specified as a tuple to compute statistics over these dimensions. A weighting vector `w` can be specified to weight the estimates. Finally, bias correction is be applied to the variance calculation if `corrected=true`. See [`var`](@ref) documentation for more details.
