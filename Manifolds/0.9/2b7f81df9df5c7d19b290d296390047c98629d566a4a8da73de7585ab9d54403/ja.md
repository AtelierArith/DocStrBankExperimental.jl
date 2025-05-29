```
project(M::Grassmann, p, X)
```

`X`を[`Grassmann`](@ref) `M`の点`p`の接空間に射影します。これは次のように計算されます。

$$
\operatorname{proj_p}(X) = X - pp^{\mathrm{H}}X,
$$

ここで、$⋅^{\mathrm{H}}$は複素共役転置またはエルミートを示します。
