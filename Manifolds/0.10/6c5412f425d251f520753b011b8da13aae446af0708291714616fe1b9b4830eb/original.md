```
convert(::Type{PoincareBallPoint}, p::PoincareHalfSpacePoint)
```

convert a point [`PoincareHalfSpacePoint`](@ref) `p` (from $ℝ^n$) from the Poincaré half plane model of the [`Hyperbolic`](@ref) manifold $\mathcal H^n$ to a [`PoincareBallPoint`](@ref) $π(p) ∈ ℝ^n$. Denote by $\tilde p = (p_1,\ldots,p_{d-1})^{\mathrm{T}}$. Then the isometry is defined by

$$
π(p) = \frac{1}{\lVert \tilde p \rVert^2 + (p_n+1)^2}
\begin{pmatrix}2p_1\\⋮\\2p_{n-1}\\\lVert p\rVert^2 - 1\end{pmatrix}.
$$
