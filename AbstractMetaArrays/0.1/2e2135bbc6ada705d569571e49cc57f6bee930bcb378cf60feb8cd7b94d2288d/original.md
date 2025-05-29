```
SimpleMetaArray(T::Type, dims::Dims{N}, metadata::DictOrNothing=nothing, colmetadata::Union{NTuple{N,DictOrNothing},DictOrNothing}=nothing) where N
SimpleMetaArray(A::Type{<:AbstractArray{T,N}}, dims::Dims{N}, metadata::DictOrNothing=nothing, colmetadata::Union{NTuple{N,DictOrNothing},DictOrNothing}=nothing) where {T,N}
```

Construct a `SimpleMetaArray` with the given type, dimensions, metadata and colmetadata. The type can be a concrete type or a comcrete subtype of `AbstractArray`.
