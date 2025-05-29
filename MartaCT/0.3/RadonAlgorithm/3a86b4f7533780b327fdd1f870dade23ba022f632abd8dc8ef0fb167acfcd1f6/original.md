```
radon(image::AbstractMatrix, geometry::AbstractGeometry[, algorithm::AbstractProjectionAlgorithm]; <keyword arguments>)
```

Compute the Radon transform of `image` with explicit geometry. Additional parameters can be passed to the algorithm through keyword arguments. Please see the relative documentation. The default algorithm is [`Radon`](@ref).

See Also: [`project_image`](@ref)
