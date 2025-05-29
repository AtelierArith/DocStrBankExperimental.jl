```
log(M::Grassmann, p, q)
```

[`Grassmann`](@ref) `M` $= \mathcal M=\mathrm{Gr}(n,k)$ 上の対数写像を計算します。すなわち、点 `p` から始まり、時間 1 で `M` 上の `q` に到達する対応する [`geodesic`](@extref `ManifoldsBase.geodesic-Tuple{AbstractManifold, Any, Any}`) の接ベクトル `X` です。式は次のようになります。

$$
\log_p q = V⋅ \operatorname{atan}(S) ⋅ U^\mathrm{H},
$$

ここで、$⋅^{\mathrm{H}}$ は複素共役転置またはエルミートを示します。行列 $U$ と $V$ はユニタリ行列であり、$S$ は SVD 分解の特異値を含む対角行列です。

$$
USV = (q^\mathrm{H}p)^{-1} ( q^\mathrm{H} - q^\mathrm{H}pp^\mathrm{H}).
$$

この式において、$\operatorname{atan}$ は要素ごとに意味されます。
