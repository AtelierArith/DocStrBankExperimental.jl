```
exp(M::GeneralizedGrassmann, p, X)
```

[`GeneralizedGrassmann`](@ref) `M` $= \mathrm{Gr}(n,k,B)$ の点 `p` で接ベクトル（方向） `X` を用いて指数写像を計算します。$X^{\mathrm{H}}BX = USV$ として $X^{\mathrm{H}}BX$ のSVD分解を示します。指数写像は次のように書かれます。

$$
\exp_p X = p V\cos(S)V^\mathrm{H} + U\sin(S)V^\mathrm{H},
$$

ここで $⋅^{\mathrm{H}}$ は複素共役転置またはエルミートを示し、コサインとサインは $S$ の対角成分に要素ごとに適用されます。
