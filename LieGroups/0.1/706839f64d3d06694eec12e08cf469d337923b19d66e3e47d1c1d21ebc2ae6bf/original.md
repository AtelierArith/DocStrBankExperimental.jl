```
get_coordinates(𝔤::OrthogonalLieAlgebra, X, ::DefaultLieAlgebraOrthogonalBasis)
get_coordinates(G::SpecialOrthogonalLieAlgebra, X, ::DefaultLieAlgebraOrthogonalBasis)
get_coordinates!(G::OrthogonalLieAlgebra, c, X ::DefaultLieAlgebraOrthogonalBasis)
get_coordinates!(G::SpecialOrthogonalLieAlgebra, c, X ::DefaultLieAlgebraOrthogonalBasis)
```

Compute the vector of coordinates $c ∈ ℝ^d$ from the Lie algebra tangent vector $X ∈ 𝔬(n)$ of the [`OrthogonalGroup`](@ref) `O(n)` in the [`DefaultLieAlgebraOrthogonalBasis`](@ref), where $d$ is the dimension of the Lie algebra. This is also the version used in [`vee`](@ref).

For $O(2)$ there is only one coefficient $α$ in the basis $\begin{pmatrix} 0 & -α\\ α & 0\end{pmatrix}$, which is returned as $c = (α)^\mathrm{T}$.

A usual basis representation of ``𝔬(3) is given by

$$
    X = \begin{pmatrix} 0 & -γ & β\\ γ & 0 & -α\\ -β & α & 0\end{pmatrix},
$$

hence the coordinate vector is $c = (α, β, γ)^\mathrm{T} ∈ ℝ^3$.

For `n ≥ 4``the lower triangular part is added to``c`` row-wise.
