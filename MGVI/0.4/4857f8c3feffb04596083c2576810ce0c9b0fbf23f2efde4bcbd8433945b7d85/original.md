```
mgvi_mvnormal_pushfwd_function(
    forward_model, data, config::MGVIConfig,
    center_point::AbstractVector{<:Real}, context::MGVIContext
)
```

Returns a function that pushes a multivariate normal distribution forward to the MGVI posterior approximation.

This currently instantiates the full Jabocian of the forward model as a matrix in memory, and so should not be used for very high-dimensional problems.
