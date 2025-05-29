```
convert(::Type{PoincareBallPoint}, p::PoincareHalfSpacePoint)
```

点 [`PoincareHalfSpacePoint`](@ref) `p`（$ℝ^n$ から）を、[`Hyperbolic`](@ref) 多様体 $\mathcal H^n$ のポアンカレ半平面モデルから [`PoincareBallPoint`](@ref) $π(p) ∈ ℝ^n$ に変換します。$\tilde p = (p_1,\ldots,p_{d-1})^{\mathrm{T}}$ とします。すると、同型は次のように定義されます。

$$
π(p) = \frac{1}{\lVert \tilde p \rVert^2 + (p_n+1)^2}
\begin{pmatrix}2p_1\\⋮\\2p_{n-1}\\\lVert p\rVert^2 - 1\end{pmatrix}.
$$
