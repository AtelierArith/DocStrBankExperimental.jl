```
project(M::SymmetricMatrices, p, X)
```

行列 `X` を [`SymmetricMatrices`](@ref) `M` の点 `p` での接空間に射影します。

$$
\operatorname{proj}_p(X) = \frac{1}{2} \bigl( X + X^{\mathrm{H}} \bigr),
$$

ここで $⋅^{\mathrm{H}}$ はエルミート、すなわち複素共役転置を示します。
