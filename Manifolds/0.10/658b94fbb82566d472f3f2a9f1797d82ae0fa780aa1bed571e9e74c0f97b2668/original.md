```
convert(::Type{PoincareHalfSpacePoint}, p::PoincareBallPoint)
```

convert a point [`PoincareBallPoint`](@ref) `p` (from $ℝ^n$) from the Poincaré ball model of the [`Hyperbolic`](@ref) manifold $\mathcal H^n$ to a [`PoincareHalfSpacePoint`](@ref) $π(p) ∈ ℝ^n$. Denote by $\tilde p = (p_1,\ldots,p_{n-1})$. Then the isometry is defined by

$$
π(p) = \frac{1}{\lVert \tilde p \rVert^2 - (p_n-1)^2}
\begin{pmatrix}2p_1\\⋮\\2p_{n-1}\\1-\lVert p\rVert^2\end{pmatrix}.
$$
