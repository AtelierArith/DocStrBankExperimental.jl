```
iradon(sinog::AbstractMatrix[, algorithm::AbstractProjectionAlgorithm]; <keyword arguments>)
```

Compute the inverse Radon transform of `sinog` with parameters given as keyword arguments. The parameters depend on the algorithm, please see the relative documentation. The default algorithm is [`FBP`](@ref).

See Also: [`reconstruct_image`](@ref)
