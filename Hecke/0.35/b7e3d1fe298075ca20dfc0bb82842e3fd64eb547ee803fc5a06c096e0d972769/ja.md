```
prime_ideals_up_to(O::AbsSimpleNumFieldOrder,
                   B::Int;
                   degree_limit::Int = 0, index_divisors::Bool = true) -> Vector{AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}}
```

ノルムが $B$ 以下の素イデアル $\mathcal O$ を計算します。

`degree_limit` が非ゼロの整数 $k$ の場合、$\deg(\mathfrak p) > k$ の素イデアル $\mathfrak p$ は除外されます。`index_divisors` が false に設定されている場合、順序の指数を割らない素数のみが計算されます。
