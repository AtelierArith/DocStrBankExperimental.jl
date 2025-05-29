```
project(M::GeneralizedGrassmann, p, X)
```

`X`を[`GeneralizedGrassmann`](@ref) `M`の点`p`の接空間に射影します。これは次のように計算されます。

$$
\operatorname{proj_p}(X) = X - pp^{\mathrm{H}}B^\mathrm{T}X,
$$

ここで、$⋅^{\mathrm{H}}$は複素共役転置またはエルミートを、$⋅^{\mathrm{T}}$は転置を示します。
