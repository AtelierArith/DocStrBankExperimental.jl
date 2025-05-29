```
mean_and_std(x, [w::AbstractWeights], [dim]; corrected=true) -> (mean, std)
```

Return the mean and standard deviation of collection `x`. If `x` is an `AbstractArray`, `dim` can be specified as a tuple to compute statistics over these dimensions. A weighting vector `w` can be specified to weight the estimates. Finally, bias correction is applied to the standard deviation calculation if `corrected=true`. See [`std`](@ref) documentation for more details.
