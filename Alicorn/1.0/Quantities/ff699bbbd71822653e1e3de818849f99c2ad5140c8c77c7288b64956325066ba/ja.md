```
QuantityArray{T}(::AbstractQuantityArray, ::InternalUnits) where {T<:Number}
QuantityArray{T}(::AbstractQuantityArray) where {T<:Number}
```

物理量の任意の `AbstractQuantityArray` の実装から、指定された型 `T` の `QuantityArray{T}` を構築します。

詳細については `QuantityArray(::AbstractQuantityArray, ::InternalUnits)` を参照してください。

# 例外を発生させる

  * `InexactError`: `AbstractQuantityArray` の内部値が型 `Array{T}` として表現できない場合。
