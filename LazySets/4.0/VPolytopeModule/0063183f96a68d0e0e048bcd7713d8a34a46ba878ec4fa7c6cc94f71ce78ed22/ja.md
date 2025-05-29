# 拡張ヘルプ

```
linear_map(M::AbstractMatrix, P::VPolytope; [apply_convex_hull]::Bool=false)
```

### 入力

  * `apply_convex_hull` – （オプション、デフォルト: `false`）冗長な頂点を排除するための凸包を適用するフラグ

### アルゴリズム

線形マップ $M$ は、与えられた集合 $P$ の各頂点に適用され、頂点表現のポリトープが得られます。出力タイプは再び `VPolytope` です。
