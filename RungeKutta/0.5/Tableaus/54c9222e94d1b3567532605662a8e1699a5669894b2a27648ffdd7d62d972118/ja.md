Radau IIB タブローと s ステージ

```julia
TableauRadauIIB(::Type{T}, s)
TableauRadauIIB(s) = TableauRadauIIB(Float64, s)
```

コンストラクタは、ステージの数 `s` とオプションでタブローの要素型 `T` を受け取ります。

係数は $a^B = \frac{1}{2} ( a^A + \bar{a}^A )$ として取られ、ここで $a^A$ は Radau IIA 法の係数であり、$\bar{a}^AV$ はシンプレクティシティ条件を満たすように計算されます。すなわち、$b*{i} \bar{a}*{i,j} + \bar{b}*{j} a*{j,i} = b*{i} \bar{b}*{j}$ および $b*{i} = \bar{b}*i$ がすべての $1 \le i,j \le s$ に対して成り立ちます。

参考文献:

```
Sun Geng
Construction of high order symplectic Runge-Kutta methods
Journal of Computational Mathematics, Volume 11, Pages 250-260, 1993.
```
