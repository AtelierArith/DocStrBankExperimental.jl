```
convert(::Type{PoincareBallPoint}, p::HyperboloidPoint)
convert(::Type{PoincareBallPoint}, p::T) where {T<:AbstractVector}
```

convert a [`HyperboloidPoint`](@ref) $p∈ℝ^{n+1}$ from the hyperboloid model of the [`Hyperbolic`](@ref) manifold $\mathcal H^n$ to a [`PoincareBallPoint`](@ref) $π(p)∈ℝ^{n}$ in the Poincaré ball model. The isometry is defined by

$$
π(p) = \frac{1}{1+p_{n+1}} \begin{pmatrix}p_1\\⋮\\p_n\end{pmatrix}
$$

Note that this is also used, when `x` is a vector.
