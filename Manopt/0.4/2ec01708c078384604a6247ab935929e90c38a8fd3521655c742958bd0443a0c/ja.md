```
cyclic_proximal_point!(M, F, proxes, p)
cyclic_proximal_point!(M, mpo, p)
```

`p`の代わりにサイクリック近接点アルゴリズムを実行します。

# 入力

  * `M`:      多様体 $\mathcal M$
  * `F`:      最小化するコスト関数 $F:\mathcal M→ℝ$
  * `proxes`: 近接写像の配列（`Function`）`(M, λ, p) -> q` または `(M, q, λ, p)` で $F$ の和項
  * `p`:      初期値 $p ∈ \mathcal M$

ここで、`f` と近接写像 `proxes_f` は [`ManifoldProximalMapObjective`](@ref) `mpo` として直接与えることもできます。

すべてのオプションについては、[`cyclic_proximal_point`](@ref) を参照してください。
