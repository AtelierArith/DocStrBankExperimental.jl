```
project(M::SymmetricMatrices, p)
```

埋め込みから [`SymmetricMatrices`](@ref) `M` への `p` の射影、すなわち

$$
\operatorname{proj}_{\operatorname{Sym}(n)}(p) = \frac{1}{2} \bigl( p + p^{\mathrm{H}} \bigr),
$$

ここで $⋅^{\mathrm{H}}$ はエルミート、すなわち複素共役転置を示します。
