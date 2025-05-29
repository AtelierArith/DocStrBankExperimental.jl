```
prime_ideals_over(O::AbsSimpleNumFieldOrder,
                   lp::AbstractVector{Int};
                   degree_limit::Int = 0) -> Vector{AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}}
```

素数 $lp$ に対する $\mathcal O$ 上の素イデアルを計算します。

`degree_limit` が非ゼロの整数 $k$ の場合、$\deg(\mathfrak p) > k$ である素イデアル $\mathfrak p$ は除外されます。
