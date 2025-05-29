SimpleMetaArray{T,N,A<:AbstractArray{T,N}} <: AbstractMetaArray{T,N,A<:AbstractArray{T,N}}

Concrete implementation of AbstractMetaArray for a simple array with metadata. This is a concrete type that can be used to create instances of AbstractMetaArray. It has metadata and colmetadata fields that are dictionaries with string keys and values of type `Tuple{Any,Symbol}`.

It uses the following traits:

AbstractMetaArrays.ColMetadataTrait(::Type{<:SimpleMetaArray}) = HasColMetadata()   AbstractMetaArrays.ColMetadataStyle(::Type{<:SimpleMetaArray}) = ReadWriteColMetadata()   AbstractMetaArrays.MetadataStyle(::Type{<:SimpleMetaArray}) = ReadWriteMetadata()

See also [`AbstractMetaArray`](@ref) for more information on the abstract type and its methods.
