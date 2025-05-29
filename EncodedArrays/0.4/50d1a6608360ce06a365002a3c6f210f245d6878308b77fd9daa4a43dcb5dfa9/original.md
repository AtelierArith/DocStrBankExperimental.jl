```
abstract type AbstractArrayCodec <: Codecs.Codec end
```

Abstract type for arrays codecs.

Subtypes must implement the [`AbstractEncodedArray`](@ref) API. Most coded should use [`EncodedArray`](@ref) as the concrete subtype of `AbstractArrayCodec`. Codecs that use a custom subtype of `AbstractEncodedArray` must implement

```
EncodedArrays.encarraytype(::Type{<:AbstractArrayCodec},::Type{<:AbstractArray{T,N}})::Type{<:AbstractEncodedArray{T,N}}
```
