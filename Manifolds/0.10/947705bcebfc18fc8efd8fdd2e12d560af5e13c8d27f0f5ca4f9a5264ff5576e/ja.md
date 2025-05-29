```
log(M::GeneralizedGrassmann, p, q)
```

[`GeneralizedGrassmann`](@ref) `M` $= \mathcal M=\mathrm{Gr}(n,k,B)$ における対数写像を計算します。すなわち、点 `p` から始まり、時間 1 で `q` に到達する対応する [`geodesic`](@extref `ManifoldsBase.geodesic-Tuple{AbstractManifold, Any, Any}`) の接ベクトル `X` です。この式は次のように表されます。

$$
\log_p q = V⋅ \operatorname{atan}(S) ⋅ U^\mathrm{H},
$$

ここで $⋅^{\mathrm{H}}$ は複素共役転置またはエルミートを示します。行列 $U$ と $V$ はユニタリ行列であり、$S$ は SVD 分解の特異値を含む対角行列です。

$$
USV = (q^\mathrm{H}Bp)^{-1} ( q^\mathrm{H} - q^\mathrm{H}Bpp^\mathrm{H}).
$$

この式において、$\operatorname{atan}$ は要素ごとに意味されます。
