```
SimpleQuantityArray{T}(quantity::AbstractQuantity) where {T<:Number}
```

指定された型 `T` の 1x1 `SimpleQuantityArray{T}` を、`AbstractQuantity` の任意の実装からの物理量を使用して構築します。

詳細については `SimpleQuantityArray(::AbstractQuantity)` を参照してください。

# 例外を発生させる

  * `InexactError`: `AbstractQuantity` の値が

型 `Array{T}` として表現できない場合。
