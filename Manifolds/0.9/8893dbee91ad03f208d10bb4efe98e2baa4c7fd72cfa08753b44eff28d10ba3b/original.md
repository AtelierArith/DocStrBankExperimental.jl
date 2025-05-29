```
convert(::Type{HyperboloidPoint}, p::PoincareBallPoint)
convert(::Type{AbstractVector}, p::PoincareBallPoint)
```

convert a point [`PoincareBallPoint`](@ref) `x` (from $ℝ^n$) from the Poincaré ball model of the [`Hyperbolic`](@ref) manifold $\mathcal H^n$ to a [`HyperboloidPoint`](@ref) $π(p) ∈ ℝ^{n+1}$. The isometry is defined by

$$
π(p) = \frac{1}{1-\lVert p \rVert^2}
\begin{pmatrix}2p_1\\⋮\\2p_n\\1+\lVert p \rVert^2\end{pmatrix}
$$

Note that this is also used, when the type to convert to is a vector.
