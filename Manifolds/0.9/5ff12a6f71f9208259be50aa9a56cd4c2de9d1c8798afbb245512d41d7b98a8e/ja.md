```
project(M::SphereSymmetricMatrices, p)
```

`p`を埋め込みから[`SphereSymmetricMatrices`](@ref) `M`に射影します。すなわち、

$$
\operatorname{proj}_{\mathcal{S}_{\text{sym}}}(p) = \frac{1}{2} \bigl( p + p^{\mathrm{H}} \bigr),
$$

ここで、$⋅^{\mathrm{H}}$はエルミート、すなわち複素共役転置を示します。
