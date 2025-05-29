```
project(M::SphereSymmetricMatrices, p)
```

Projects `p` from the embedding onto the [`SphereSymmetricMatrices`](@ref) `M`, i.e.

$$
\operatorname{proj}_{\mathcal{S}_{\text{sym}}}(p) = \frac{1}{2} \bigl( p + p^{\mathrm{H}} \bigr),
$$

where $⋅^{\mathrm{H}}$ denotes the Hermitian, i.e. complex conjugate transposed.
