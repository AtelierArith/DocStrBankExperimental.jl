```
radon(image::AbstractMatrix, ts, ϕs[, algorithm::AbstractProjectionAlgorithm]; <keyword arguments>)
```

Compute the Radon transform of `image` with integration points given by the vector `ts` and projection angles given by the vector `ϕs`. Additional parameters can be passed to the algorithm through keyword arguments.Please see the relative documentation. The default algorithm is [`Radon`](@ref).

See Also: [`project_image`](@ref)
