```
default_vector_transport_method(M::AbstractManifold)
default_vector_transport_method(M::AbstractManifold, ::Type{T}) where {T}
```

The [`AbstractVectorTransportMethod`](@ref) that is used when calling [`vector_transport_to`](@ref) or [`vector_transport_direction`](@ref) without specifying the vector transport method. By default, this is [`ParallelTransport`](@ref).

This method can also be specified more precisely with a point type `T`, for the case that on a `M` there are two different representations of points, which provide different vector transport methods.
