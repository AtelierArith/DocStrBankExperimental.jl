```
project(M::SphereSymmetricMatrices, p, X)
```

Project the matrix `X` onto the tangent space at `p` on the [`SphereSymmetricMatrices`](@ref) `M`, i.e.

$$
\operatorname{proj}_p(X) = \frac{X + X^{\mathrm{H}}}{2} - ⟨p, \frac{X + X^{\mathrm{H}}}{2}⟩p,
$$

where $⋅^{\mathrm{H}}$ denotes the Hermitian, i.e. complex conjugate transposed.
