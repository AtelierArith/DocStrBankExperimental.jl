```
Quantity{T}(::AbstractQuantity, ::InternalUnits) where {T<:Number}
Quantity{T}(::AbstractQuantity) where {T<:Number}
```

指定された型 `T` を持つ `Quantity{T}` を、`AbstractQuantity` の任意の実装からの物理量から構築します。

詳細については `Quantity(::AbstractQuantity, ::InternalUnits)` を参照してください。

# 例外を発生させる

  * `InexactError`: `AbstractQuantity` の内部値が型 `T` として表現できない場合。
