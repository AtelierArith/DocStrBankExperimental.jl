```
isapprox(x::FixedPoint, y::FixedPoint; rtol=0, atol=max(eps(x), eps(y)))
```

FixedPoint 数に対して、デフォルトの基準は `x` と `y` が隣接する固定小数点数の間隔である `eps` を超えて異ならないことです。
