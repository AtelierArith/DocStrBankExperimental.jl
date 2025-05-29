```
project(M::SkewHermitianMatrices, p)
```

Projects `p` from the embedding onto the [`SkewHermitianMatrices`](@ref) `M`, i.e.

$$
\operatorname{proj}_{\operatorname{SkewHerm}(n)}(p) = \frac{1}{2} \bigl( p - p^{\mathrm{H}} \bigr),
$$

where $⋅^{\mathrm{H}}$ denotes the Hermitian, i.e. complex conjugate transposed.
