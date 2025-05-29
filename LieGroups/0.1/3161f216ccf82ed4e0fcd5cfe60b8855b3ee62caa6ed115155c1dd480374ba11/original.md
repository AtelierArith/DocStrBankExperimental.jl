```
vee(𝔤::LieAlgebra, X)
vee!(𝔤::LieAlgebra, c, X)
```

Compute the vee map $(⋅){\vee}: \mathfrak g → \mathcal V$ that maps a tangent vector `X` from the [`LieAlgebra`](@ref) \mathfrak g to its coordinates with respect to the [`DefaultLieAlgebraOrthogonalBasis`](@ref) basis in the Lie algebra

$$
X = \sum_{i∈\mathcal I} c_iB_i,
$$

where $\{ B_i \}_{i∈\mathcal I}$ is a basis of the Lie algebra and $\mathcal I$ a corresponding index set, which is usually $\mathcal I=\{ 1,\ldots,n \}$. Then $\mathcal V = ℝ^n$

The computation can be performed in-place of `c`. The inverse of `vee` is [`hat`](@ref). Technically, `vee` is a specific case of [`get_coordinates`](@ref) and is implemented using the [`DefaultLieAlgebraOrthogonalBasis`](@ref).
