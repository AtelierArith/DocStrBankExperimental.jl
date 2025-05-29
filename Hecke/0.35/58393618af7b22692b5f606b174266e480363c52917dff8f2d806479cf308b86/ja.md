```
prime_ideals_over(O::AbsSimpleNumFieldOrder,
                   lp::AbstractVector{Int};
                   degree_limit::Int = 0) -> Vector{AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}}
```

素数 $lp$ に対する素理想 $\mathcal O$ を計算します。

`degree_limit` が非ゼロ整数 $k$ の場合、$\deg(\mathfrak p) > k$ となる素理想 $\mathfrak p$ は除外されます。
