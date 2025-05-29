```
get_vector(G::OrthogonalLieAlgebra, e, c, ::DefaultLieAlgebraOrthogonalBasis)
get_vector(G::SpecialOrthogonalLieAlgebra, e, c, ::DefaultLieAlgebraOrthogonalBasis)
get_vector!(G::OrthogonalLieAlgebra, X, e, c, ::DefaultLieAlgebraOrthogonalBasis)
get_vector!(G::SpecialOrthogonalLieAlgebra, X, e, c, ::DefaultLieAlgebraOrthogonalBasis)
```

Compute the tangent vector $X ∈ 𝔬(n)$ based on a vector of coordinates $c ∈ ℝ^d$, where $d$ is the dimension of the Lie algebra of the [`OrthogonalGroup`](@ref) `O(n)` and the coordinates are with respect to the [`DefaultLieAlgebraOrthogonalBasis`](@ref). This is also the version used in [`hat`](@ref).

For $O(2)$ there is only one coefficient ``$c = (α)^\mathrm{T}$ and hence $X = \begin{pmatrix} 0 & -α\\ α & 0\end{pmatrix}$ is returned.

For $n=3$ a usual representtion turns $c = (α, β, γ)^\mathrm{T} ∈ ℝ^3$ into

$$
    X = \begin{pmatrix} 0 & -γ & β\\ γ & 0 & -α\\ -β & α & 0\end{pmatrix},
$$

hence the coordinate vector is .

For `n ≥ 4`` all further coefficients are used to fill up the following rows of the lower triangular part – which determines the upper triangular part due to skew-symmetry
