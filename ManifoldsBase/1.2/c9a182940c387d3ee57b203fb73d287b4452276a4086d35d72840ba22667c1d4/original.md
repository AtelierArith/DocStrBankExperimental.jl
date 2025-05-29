```
VectorTransportDirection{VM<:AbstractVectorTransportMethod,RM<:AbstractRetractionMethod}
    <: AbstractVectorTransportMethod
```

Specify a [`vector_transport_direction`](@ref) using a [`AbstractVectorTransportMethod`](@ref) with explicitly using the [`AbstractRetractionMethod`](@ref) to determine the point in the specified direction where to transsport to. Note that you only need this for the non-default (non-implicit) second retraction method associated to a vector transport, i.e. when a first implementation assumed an implicit associated retraction.
