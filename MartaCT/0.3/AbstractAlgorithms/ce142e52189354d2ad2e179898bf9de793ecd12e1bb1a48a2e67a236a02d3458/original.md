```
iradon(sinog::AbstractMatrix[, geometry::AbstractGeometry[, params::AbstractParams[, algorithm::AbstractProjectionAlgorithm]]]; <keyword arguments>)
```

Compute the inverse Radon transform of `sinog` with explicit geometry. If the algorithm needs specific parameters, these can be passed with `params`. Additional parameters can be passed to the algorithm through keyword arguments. Please see the respective documentation for more details. The default algorithm is [`FBP`](@ref).

See Also: [`reconstruct_image`](@ref)
