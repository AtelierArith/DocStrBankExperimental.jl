```
EncodedArray{T,N,C,DV} <: AbstractEncodedArray{T,N}
```

Concrete type for [`AbstractEncodedArray`](@ref)s.

Constructor:

```julia
EncodedArray{T}(
    codec::AbstractArrayCodec,
    size::NTuple{N,Integer},
    encoded::AbstractVector{UInt8}
)
```

Codecs using `EncodedArray` only need to implement [`EncodedArrays.encode_data!`](@ref) and [`EncodedArrays.decode_data!`](@ref).

If length of the decoded data can be inferred from the encoded data, a constructor

```
EncodedArray{T,N}(codec::MyCodec,encoded::AbstractVector{UInt8})
```

should also be defined. By default, two `EncodedArray`s that have the same codec and size are assumed to be equal if and only if their code units are equal.

Generic methods for the rest of the [`AbstractEncodedArray`](@ref) API are already provided for `EncodedArray`. 
