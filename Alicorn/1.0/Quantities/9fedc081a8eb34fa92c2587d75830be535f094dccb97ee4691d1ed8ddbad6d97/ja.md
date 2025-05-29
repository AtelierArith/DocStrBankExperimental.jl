```
QuantityArray{T<:Number,N} <: AbstractQuantityArray{T,N}
```

物理量は、配列、物理次元を表す `Dimension` オブジェクト、および SI システムの7つの基本次元に対して測定される単位を表す `InternalUnits` オブジェクトで構成されています。

`QuantityArray{T,N}` の値フィールドは `Array{T,N}` 型です。`T` は `Number` のサブタイプである必要があります。

# フィールド

  * `value::Array{T,N}`: 量の値
  * `dimension::Dimension`: 量の物理次元
  * `internalUnits::InternalUnits`: SI システムの7つの基本次元に対して測定される単位のセット

# コンストラクタ

```
QuantityArray(::AbstractArray, ::Dimension, ::InternalUnits)
QuantityArray(::AbstractArray, ::Dimension)
QuantityArray(::AbstractArray, ::InternalUnits)
QuantityArray(::AbstractArray)
```

コンストラクタに `InternalUnits` が渡されない場合、基本 SI 単位が使用されます。コンストラクタに `Dimension` が渡されない場合、次元のない量が構築されます。

```
QuantityArray{T}(::AbstractArray, ::Dimension, ::InternalUnits) where {T<:Number}
QuantityArray{T}(::AbstractArray, ::Dimension) where {T<:Number}
QuantityArray{T}(::AbstractArray, ::InternalUnits) where {T<:Number}
QuantityArray{T}(::AbstractArray) where {T<:Number}
```

型 `T` が明示的に指定されている場合、Alicorn は提供された `AbstractArray` を `Array{T}` に変換しようとします。
