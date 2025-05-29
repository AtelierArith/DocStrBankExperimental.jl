```
convert(::Type{PoincareBallTVector}, p::HyperboloidPoint, X::HyperboloidTVector)
convert(::Type{PoincareBallTVector}, p::P, X::T) where {P<:AbstractVector, T<:AbstractVector}
```

convert a [`HyperboloidTVector`](@ref) `X` at `p` to a [`PoincareBallTVector`](@ref) on the [`Hyperbolic`](@ref) manifold $\mathcal H^n$ by computing the push forward $π_*(p)[X]$ of the isometry $π$ that maps from the Hyperboloid to the Poincaré ball, cf. [`convert(::Type{PoincareBallPoint}, ::HyperboloidPoint)`](@ref).

The formula reads

$$
π_*(p)[X] = \frac{1}{p_{n+1}+1}\Bigl(\tilde X - \frac{X_{n+1}}{p_{n+1}+1}\tilde p \Bigl),
$$

where $\tilde X = \begin{pmatrix}X_1\\⋮\\X_n\end{pmatrix}$ and $\tilde p = \begin{pmatrix}p_1\\⋮\\p_n\end{pmatrix}$.
