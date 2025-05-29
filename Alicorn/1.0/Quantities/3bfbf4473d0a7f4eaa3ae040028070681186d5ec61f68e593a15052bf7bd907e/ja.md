```
SimpleQuantityArray{T<:Number,N} <: AbstractQuantityArray{T,N}
```

数値配列と物理単位からなる物理量。

`SimpleQuantityArray{T,N}`の値フィールドは`Array{T,N}`型です。`T`は`Number`のサブタイプである必要があります。

# フィールド

  * `value::Array{T,N}`: 量の値
  * `unit::Unit`: 量の単位

# コンストラクタ

```
SimpleQuantityArray(::AbstractArray, ::AbstractUnit)
SimpleQuantityArray(::AbstractArray)
```

コンストラクタに単位が渡されない場合、デフォルトで`unitlessUnit`が使用されます。

```
SimpleQuantityArray{T}(::AbstractArray, ::AbstractUnit) where {T<:Number}
SimpleQuantityArray{T}(::AbstractArray) where {T<:Number}
```

型`T`が明示的に指定されている場合、Alicornはそれに応じて`value`を変換しようとします。
