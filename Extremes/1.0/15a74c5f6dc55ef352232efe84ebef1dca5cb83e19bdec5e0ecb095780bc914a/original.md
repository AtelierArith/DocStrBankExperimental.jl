```
mrlplot_data(y::Vector{<:Real}, steps::Int = 100)::DataFrame
```

Compute the mean residual life from vector `y`.

The set of thresholds ranges from `minimum(y)` to the second-to-last larger value in `steps` number of steps.
