```
project(M::SymmetricMatrices, p)
```

Projects `p` from the embedding onto the [`SymmetricMatrices`](@ref) `M`, i.e.

$$
\operatorname{proj}_{\operatorname{Sym}(n)}(p) = \frac{1}{2} \bigl( p + p^{\mathrm{H}} \bigr),
$$

where $⋅^{\mathrm{H}}$ denotes the Hermitian, i.e. complex conjugate transposed.
