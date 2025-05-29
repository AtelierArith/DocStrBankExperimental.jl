```
gradient(coord::AbstractVector{C}, arr::AbstractVector{A}; method::Symbol=:second_order) where {C<:Real, A<:Real}
```

有限差分勾配。返される勾配は入力配列と同じ形状を持ちます。

勾配の`method`は、[:backward, :central, :forward, :second*order, :third*order]のいずれかです。

`:central`の場合、勾配は内部点で二次精度の中央差分を使用して計算され、境界では一次精度の片側（前方または後方）差分が使用されます。

`:second_order`の場合、勾配は内部点で二次精度の中央差分を使用して計算され、境界では二次差分が使用されます。

`:third_order`の場合、勾配は点を通る三次スプラインから計算されます。
