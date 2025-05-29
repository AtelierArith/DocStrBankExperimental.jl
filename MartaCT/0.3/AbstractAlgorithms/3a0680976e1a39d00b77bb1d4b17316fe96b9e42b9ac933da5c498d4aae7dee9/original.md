```
iradon(sinog::AbstractMatrix, xs[, ys[, algorithm::AbstractProjectionAlgorithm[, coo::AbstractCoordinates]]]; <keyword arguments>)
```

Compute the inverse Radon transform of `sinog` on the points given by the vectors `xs` and `ys`. If `ys` is omitted, the reconstruction is performed on the square with `xs == ys`. The default reconstruction algorithm is [`FBP`](@ref). Please refer to the respective documentation for additional parameters.

See Also: [`reconstruct_image`](@ref)
