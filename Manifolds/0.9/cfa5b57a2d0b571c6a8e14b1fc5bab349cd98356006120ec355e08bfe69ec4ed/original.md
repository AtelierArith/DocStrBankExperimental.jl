```
project(M::SymmetricMatrices, p, X)
```

Project the matrix `X` onto the tangent space at `p` on the [`SymmetricMatrices`](@ref) `M`,

$$
\operatorname{proj}_p(X) = \frac{1}{2} \bigl( X + X^{\mathrm{H}} \bigr),
$$

where $⋅^{\mathrm{H}}$ denotes the Hermitian, i.e. complex conjugate transposed.
