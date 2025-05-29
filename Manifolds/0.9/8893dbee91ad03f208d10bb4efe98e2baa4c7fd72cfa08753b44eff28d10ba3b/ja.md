```
convert(::Type{HyperboloidPoint}, p::PoincareBallPoint)
convert(::Type{AbstractVector}, p::PoincareBallPoint)
```

点 [`PoincareBallPoint`](@ref) `x`（$ℝ^n$ から）を、[`Hyperbolic`](@ref) 多様体 $\mathcal H^n$ のポアンカレボールモデルから [`HyperboloidPoint`](@ref) $π(p) ∈ ℝ^{n+1}$ に変換します。等距変換は次のように定義されます。

$$
π(p) = \frac{1}{1-\lVert p \rVert^2}
\begin{pmatrix}2p_1\\⋮\\2p_n\\1+\lVert p \rVert^2\end{pmatrix}
$$

変換先の型がベクトルである場合にも、これが使用されることに注意してください。
