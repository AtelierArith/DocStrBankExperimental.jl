```
c = vee(𝔤::LieAlgebra{ℝ,MatrixMultiplicationGroupOperation,<:SpecialLinearGroup}, X)
vee!(𝔤::LieAlgebra{ℝ,MatrixMultiplicationGroupOperation,<:SpecialLinearGroup}, c, X)
```

Compute the vee map $(⋅)^{\vee}: \mathfrak g →  ℝ^{n^2-1}$ that maps a tangent vector from the Lie algebra to a vector of coordinates `c`.

The formula on the Lie algebra $𝔤$ of the [`SpecialLinearGroup`](@ref)`(n)` is given by reshaping $X ∈ ℝ^{n×n}$ into a vector and omitting the last entry, since that can be reconstructed by considering that $X$ has to be of trace zero.

This can be computed in-place of `c`.
