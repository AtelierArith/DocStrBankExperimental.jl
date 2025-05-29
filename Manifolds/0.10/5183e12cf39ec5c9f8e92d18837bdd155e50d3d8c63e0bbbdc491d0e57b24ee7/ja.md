```
inner(::SymplecticMatrices{<:Any,ℝ}, p, X, Y)
```

標準リーマン内積 [`RealSymplecticMetric`](@ref) を計算します。

$$
    g_p(X, Y) = \operatorname{tr}((p^{-1}X)^{\mathrm{T}} (p^{-1}Y))
$$

2つの接ベクトル $X, Y \in T_p\mathrm{Sp}(2n)$ の間で。
