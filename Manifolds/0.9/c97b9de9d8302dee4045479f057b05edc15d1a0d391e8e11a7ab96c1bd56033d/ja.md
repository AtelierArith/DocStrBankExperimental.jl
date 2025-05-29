```
exp(M::SymplecticMatrices, p, X)
exp!(M::SymplecticMatrices, q, p, X)
```

リーマン計量 [`RealSymplecticMetric`](@ref) を持つシンプレクティック多様体上の指数写像。

点 $p \in \mathrm{Sp}(2n)$ に対して、接ベクトル $X \in T_p\mathrm{Sp}(2n)$ に沿った指数写像は [WangSunFiori:2018](@cite) によって次のように計算されます。

$$
    \operatorname{exp}_p(X) = p \operatorname{Exp}((p^{-1}X)^{\mathrm{T}})
                                \operatorname{Exp}(p^{-1}X - (p^{-1}X)^{\mathrm{T}}),
$$

ここで、$\operatorname{Exp}(⋅)$ は行列の指数関数を示します。
