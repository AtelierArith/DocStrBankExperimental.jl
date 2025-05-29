```
project(M::SkewHermitianMatrices, p, X)
```

行列 `X` を [`SkewHermitianMatrices`](@ref) `M` の点 `p` における接空間に射影します。

$$
\operatorname{proj}_p(X) = \frac{1}{2} \bigl( X - X^{\mathrm{H}} \bigr),
$$

ここで $⋅^{\mathrm{H}}$ はエルミート、すなわち複素共役転置を示します。
