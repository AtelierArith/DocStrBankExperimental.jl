```
SimpleQuantityArray{T}(::AbstractQuantityArray) where {T<:Number}
```

指定された型 `T` の `SimpleQuantityArray{T}` を、`AbstractQuantityArray` の任意の実装から物理量を使用して構築します。

詳細については `SimpleQuantityArray(::AbstractQuantityArray)` を参照してください。

# 例外を発生させる

  * `InexactError`: `AbstractQuantityArray` の値が型 `Array{T}` として表現できない場合。
