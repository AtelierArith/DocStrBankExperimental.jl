```
hat(G::LieAlgebra, c)
hat(G::LieAlgebra, c, T::Type)
hat!(G::LieAlgebra, X::T, c)
```

Compute the hat map $(⋅)^{\wedge}: \mathcal V → 𝔤$ that maps a vector of coordinates $\mathbf{c} ∈ \mathcal V$, to a tangent vector $X ∈ \mathfrak g$. The coefficients are given with respect to a specific basis to a tangent vector in the Lie algebra

$$
X = \sum_{i∈\mathcal I} c_iB_i,
$$

where $\{ B_i \}_{i∈\mathcal I}$ is a basis of the Lie algebra and $\mathcal I$ a corresponding index set, which is usually $\mathcal I=\{ 1,\ldots,n \}$. Then $\mathcal V = ℝ^n$.

For the allocating variant, you can specify the type `T` of the tangent vector to obtain, in case there are different representations. The first signature produces the default representation.

The computation can be performed in-place of `X`. The inverse of `hat` is [`vee`](@ref). Technically, `hat` is a specific case of [`get_vector`](@ref) and is implemented using the [`DefaultLieAlgebraOrthogonalBasis`](@ref).
