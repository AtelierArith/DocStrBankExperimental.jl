```
vrmse(x::AbstractArray, y::AbstractArray; dims=:)
```

Compute the square root of the mean squared error between the vectors corresponding to the slices along the dimension `dims`. More efficient than `sqrt.(vmse(...))` as the `sqrt` operation is performed at the point of generation, thereby eliminating the full traversal which would otherwise occur.

See also: [`vmse`](@ref)
