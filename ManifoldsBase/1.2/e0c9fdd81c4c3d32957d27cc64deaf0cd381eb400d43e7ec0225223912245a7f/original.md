```
VectorTransportTo{VM<:AbstractVectorTransportMethod,RM<:AbstractRetractionMethod}
    <: AbstractVectorTransportMethod
```

Specify a [`vector_transport_to`](@ref) using a [`AbstractVectorTransportMethod`](@ref) with explicitly using the [`AbstractInverseRetractionMethod`](@ref) to determine the direction that transports from  in `p`to `q`. Note that you only need this for the non-default (non-implicit) second retraction method associated to a vector transport, i.e. when a first implementation assumed an implicit associated retraction.
