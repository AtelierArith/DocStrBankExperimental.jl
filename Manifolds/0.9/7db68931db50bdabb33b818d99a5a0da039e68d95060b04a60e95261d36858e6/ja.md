```
project(G::SpecialUnitary, p)
```

プロジェクト `p` を [`SpecialUnitary`](@ref) グループ `G` の最近接点に投影します。

特異値分解 $p = U S V^\mathrm{H}$ を考え、特異値は降順にソートされています。このとき、投影は次のようになります。

$$
\operatorname{proj}_{\mathrm{SU}(n)}(p) =
U\operatorname{diag}\left[1,1,…,\det(U V^\mathrm{H})\right] V^\mathrm{H}.
$$

対角行列は、結果の行列式が $+1$ であることを保証します。
