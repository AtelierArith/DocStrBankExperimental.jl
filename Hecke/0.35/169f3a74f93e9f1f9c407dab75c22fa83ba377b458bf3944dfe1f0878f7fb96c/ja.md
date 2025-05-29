```
prime_ideals_up_to(O::AbsSimpleNumFieldOrder,
                   B::Int;
                   complete::Bool = false,
                   degree_limit::Int = 0,
                   F::Function,
                   bad::ZZRingElem)
```

ノルムが $B$ 以下の素イデアル $\mathcal O$ を計算します。

`degree_limit` が非ゼロの整数 $k$ の場合、$\deg(\mathfrak p) > k$ である素イデアル $\mathfrak p$ は除外されます。

関数 $F$ は、`bad` を割らない素数に対する関数であり、すべての素イデアル $\mathfrak p$ が $p$ の上にある場合に $F(p) = \deg(\mathfrak p)$ となる必要があります。
