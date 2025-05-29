```
project(M::Rotations, p; check_det = true)
```

マンifold `M` 上の最近接点に `p` を射影します。

特異値分解 $p = U Σ V^\mathrm{T}$ を考え、特異値は降順にソートされています。このとき、射影は次のようになります。

$$
\operatorname{proj}_{\mathrm{SO}(n)}(p) =
U\operatorname{diag}\left[1,1,…,\det(U V^\mathrm{T})\right] V^\mathrm{T}
$$

対角行列は、結果の行列式が $+1$ であることを保証します。`p` がほぼ特別直交であると予想される場合は、`check_det = false` を指定することでこのチェックを回避できます。
