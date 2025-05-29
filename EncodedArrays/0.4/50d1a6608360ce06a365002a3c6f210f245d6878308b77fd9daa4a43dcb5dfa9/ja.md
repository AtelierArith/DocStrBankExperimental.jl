```
abstract type AbstractArrayCodec <: Codecs.Codec end
```

配列コーデックのための抽象型。

サブタイプは [`AbstractEncodedArray`](@ref) API を実装する必要があります。ほとんどのコーデックは `AbstractArrayCodec` の具体的なサブタイプとして [`EncodedArray`](@ref) を使用するべきです。`AbstractEncodedArray` のカスタムサブタイプを使用するコーデックは、次のように実装する必要があります。

```
EncodedArrays.encarraytype(::Type{<:AbstractArrayCodec},::Type{<:AbstractArray{T,N}})::Type{<:AbstractEncodedArray{T,N}}
```
