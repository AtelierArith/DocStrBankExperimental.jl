```
inner(M::GeneralizedGrassmann, p, X, Y)
```

2つの接ベクトル `X`、`Y` の内積を計算します。これらは [`GeneralizedGrassmann`](@ref) 多様体 `M` の点 `p` の接空間からのものです。式は次のようになります。

$$
g_p(X,Y) = \operatorname{tr}(X^{\mathrm{H}}BY),
$$

ここで、$⋅^{\mathrm{H}}$ は複素共役転置またはエルミートを示します。
