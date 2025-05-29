```
radon(image::AbstractMatrix[, algorithm::AbstractProjectionAlgorithm]; <keyword arguments>)
```

Compute the Radon transform of `image` with parameters given as keyword arguments. The parameters depend on the algorithm, please see the relative documentation. The default algorithm is [`Radon`](@ref).

See Also: [`project_image`](@ref)
