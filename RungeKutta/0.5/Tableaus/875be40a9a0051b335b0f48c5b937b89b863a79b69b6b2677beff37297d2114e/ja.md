Radau IB tableau with s stages

```julia
TableauRadauIB(::Type{T}, s)
TableauRadauIB(s) = TableauRadauIB(Float64, s)
```

コンストラクタは、ステージ数 `s` とオプションでタブローの要素型 `T` を受け取ります。

係数は $a^B = \frac{1}{2} ( a^A + \bar{a}^A )$ として取られ、ここで $a^A$ はRadau IA法の係数であり、$\bar{a}^A$ はシンプレクティシティ条件 $b_{i} \bar{a}_{i,j} + \bar{b}_{j} a_{j,i} = b_{i} \bar{b}_{j}$ および $b_{i} = \bar{b}_i$ がすべての $1 \le i,j \le s$ に対して成り立つように計算されます。

参考文献:

```
Sun Geng
Construction of high order symplectic Runge-Kutta methods
Journal of Computational Mathematics, Volume 11, Pages 250-260, 1993.
```
