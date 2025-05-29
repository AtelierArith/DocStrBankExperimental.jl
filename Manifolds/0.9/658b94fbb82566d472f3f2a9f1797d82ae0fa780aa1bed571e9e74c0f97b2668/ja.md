```
convert(::Type{PoincareHalfSpacePoint}, p::PoincareBallPoint)
```

点 [`PoincareBallPoint`](@ref) `p` を Poincaré ボールモデルから [`PoincareHalfSpacePoint`](@ref) $π(p) ∈ ℝ^n$ に変換します。ここで、$ℝ^n$ は [`Hyperbolic`](@ref) 多様体 $\mathcal H^n$ です。$\tilde p = (p_1,\ldots,p_{n-1})$ とします。すると、同型写像は次のように定義されます。

$$
π(p) = \frac{1}{\lVert \tilde p \rVert^2 - (p_n-1)^2}
\begin{pmatrix}2p_1\\⋮\\2p_{n-1}\\1-\lVert p\rVert^2\end{pmatrix}.
$$
