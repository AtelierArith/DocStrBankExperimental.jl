```
project(M::SphereSymmetricMatrices, p, X)
```

行列 `X` を [`SphereSymmetricMatrices`](@ref) `M` の点 `p` での接空間に射影します。すなわち、

$$
\operatorname{proj}_p(X) = \frac{X + X^{\mathrm{H}}}{2} - ⟨p, \frac{X + X^{\mathrm{H}}}{2}⟩p,
$$

ここで $⋅^{\mathrm{H}}$ はエルミート、すなわち複素共役転置を示します。
