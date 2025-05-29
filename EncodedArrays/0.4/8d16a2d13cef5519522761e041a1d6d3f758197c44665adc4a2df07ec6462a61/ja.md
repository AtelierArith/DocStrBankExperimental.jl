```
EncodedArray{T,N,C,DV} <: AbstractEncodedArray{T,N}
```

[`AbstractEncodedArray`](@ref)の具体的な型です。

コンストラクタ:

```julia
EncodedArray{T}(
    codec::AbstractArrayCodec,
    size::NTuple{N,Integer},
    encoded::AbstractVector{UInt8}
)
```

`EncodedArray`を使用するコーデックは、[`EncodedArrays.encode_data!`](@ref)と[`EncodedArrays.decode_data!`](@ref)を実装する必要があります。

デコードされたデータの長さがエンコードされたデータから推測できる場合、次のコンストラクタも定義する必要があります。

```
EncodedArray{T,N}(codec::MyCodec,encoded::AbstractVector{UInt8})
```

デフォルトでは、同じコーデックとサイズを持つ二つの`EncodedArray`は、そのコードユニットが等しい場合に限り等しいと見なされます。

残りの[`AbstractEncodedArray`](@ref) APIのための一般的なメソッドは、すでに`EncodedArray`に対して提供されています。
