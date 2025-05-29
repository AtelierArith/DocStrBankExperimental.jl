```
iswithinerrorbars(a, b, δ[, print=false])
```

数値 `a` と `b` が与えられた誤差 `δ` まで等しいかどうかをチェックします。`print=true` の場合は `x ≈ y + k·δ` を出力します。

`isapprox(a,b,atol=δ,rtol=zero(b))` と同等です。
