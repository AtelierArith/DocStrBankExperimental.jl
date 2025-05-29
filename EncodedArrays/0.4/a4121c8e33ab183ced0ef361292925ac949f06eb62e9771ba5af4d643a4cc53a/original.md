```
AbstractEncodedArray{T,N} <: AbstractArray{T,N}
```

Abstract type for arrays that store their elements in encoded/compressed form.

In addition to the standard `AbstractArray` API, an `AbstractEncodedArray` must support the functions

  * `EncodedArrays.getcodec(A::EncodedArray)`: Returns the codec.
  * `Base.codeunits(A::EncodedArray)`: Returns the internal encoded data representation.

Encoded arrays will typically be created via

```
A_enc = (codec::AbstractArrayCodec)(A::AbstractArray)
```

or

```
A_enc = AbstractEncodedArray(undef, codec::AbstractArrayCodec)
append!(A_enc, B::AbstractArray)
```

Decoding happens via standard array conversion or assignment:

```
A_dec = Array(A)
A_dec = convert(Array,A)
A_dec = A[:]

A_dec = Array{T,N}(undef, size(A_enc)...)
A_dec[:] = A_enc
```
