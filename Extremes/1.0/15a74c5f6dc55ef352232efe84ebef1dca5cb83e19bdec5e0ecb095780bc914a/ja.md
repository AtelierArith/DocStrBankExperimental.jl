```
mrlplot_data(y::Vector{<:Real}, steps::Int = 100)::DataFrame
```

ベクトル `y` から平均残余寿命を計算します。

閾値のセットは `minimum(y)` から `steps` 回のステップでの2番目に大きい値までの範囲です。
