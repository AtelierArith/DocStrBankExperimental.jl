```
vec(px)
```

内部の `Dict` ベースの表現から `BilateralParcellation` を `Vector{T}` に変換します。`T` は `zeros(T, ...)` メソッドを持っている必要があります。警告: これは、任意の `Parcel` が重なっている場合には適切な表現ではありません。
