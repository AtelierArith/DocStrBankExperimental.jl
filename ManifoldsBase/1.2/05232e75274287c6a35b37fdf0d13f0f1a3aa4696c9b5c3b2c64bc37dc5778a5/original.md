```
default_inverse_retraction_method(M::AbstractManifold)
default_inverse_retraction_method(M::AbstractManifold, ::Type{T}) where {T}
```

The [`AbstractInverseRetractionMethod`](@ref) that is used when calling [`inverse_retract`](@ref) without specifying the inverse retraction method. By default, this is the [`LogarithmicInverseRetraction`](@ref).

This method can also be specified more precisely with a point type `T`, for the case that on a `M` there are two different representations of points, which provide different inverse retraction methods.
