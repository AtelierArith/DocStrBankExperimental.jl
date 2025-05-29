```
default_retraction_method(M::AbstractManifold)
default_retraction_method(M::AbstractManifold, ::Type{T}) where {T}
```

The [`AbstractRetractionMethod`](@ref) that is used when calling [`retract`](@ref) without specifying the retraction method. By default, this is the [`ExponentialRetraction`](@ref).

This method can also be specified more precisely with a point type `T`, for the case that on a `M` there are two different representations of points, which provide different retraction methods.
