```
QuantityArray{T}(::AbstractQuantity, ::InternalUnits) where {T<:Number}
QuantityArray{T}(::AbstractQuantity) where {T<:Number}
```

指定された型 `T` の `QuantityArray{T}` を、`AbstractQuantity` の任意の実装から物理量を使用して構築します。

詳細については `QuantityArray(::AbstractQuantity, ::InternalUnits)` を参照してください。

# 例外を発生させる

  * `InexactError`: `AbstractQuantityArray` の内部値が型 `Array{T}` として表現できない場合。
