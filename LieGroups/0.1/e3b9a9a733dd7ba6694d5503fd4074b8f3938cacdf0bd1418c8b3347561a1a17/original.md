```
X = hat(𝔤::LieAlgebra{ℝ,MatrixMultiplicationGroupOperation,<:SpecialLinearGroup}, c)
hat!(𝔤::LieAlgebra{ℝ,MatrixMultiplicationGroupOperation,<:SpecialLinearGroup}, X, c)
```

Compute the hat map $(⋅)^{\wedge} : ℝ^{n^2-1} → 𝔤$ that turns a vector of coordinates `c` into a tangent vector in the Lie algebra.

The formula on the Lie algebra $𝔤$ of the [`SpecialLinearGroup`](@ref)`(n)` is given by reshaping $c ∈ ℝ^{n^2-1}$ into an $n$-by$n$ matrix $X$ with the final entry `X[n,n]` initialised to zero and then set to the trace of this initial matrix.

This can be computed in-place of `X`.
