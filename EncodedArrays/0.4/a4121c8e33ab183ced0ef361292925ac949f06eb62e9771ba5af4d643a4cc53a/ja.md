```
AbstractEncodedArray{T,N} <: AbstractArray{T,N}
```

エンコードされた/圧縮された形式で要素を格納する配列の抽象型です。

標準の `AbstractArray` API に加えて、`AbstractEncodedArray` は次の関数をサポートする必要があります。

  * `EncodedArrays.getcodec(A::EncodedArray)`: コーデックを返します。
  * `Base.codeunits(A::EncodedArray)`: 内部のエンコードデータ表現を返します。

エンコードされた配列は通常、次のように作成されます。

```
A_enc = (codec::AbstractArrayCodec)(A::AbstractArray)
```

または

```
A_enc = AbstractEncodedArray(undef, codec::AbstractArrayCodec)
append!(A_enc, B::AbstractArray)
```

デコードは標準の配列変換または代入を介して行われます。

```
A_dec = Array(A)
A_dec = convert(Array,A)
A_dec = A[:]

A_dec = Array{T,N}(undef, size(A_enc)...)
A_dec[:] = A_enc
```
