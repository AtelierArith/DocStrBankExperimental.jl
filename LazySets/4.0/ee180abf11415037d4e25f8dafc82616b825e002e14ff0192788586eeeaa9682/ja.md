```
vertices_list(cup::UnionSet; [apply_convex_hull]::Bool=false,
              [backend]=nothing)
```

二つの集合の和集合の頂点のリストを返します。

### 入力

  * `cup`               – 二つの集合の和集合
  * `apply_convex_hull` – （オプション、デフォルト: `false`）`true`の場合、頂点を凸包アルゴリズムを使用して後処理します
  * `backend`           – （オプション、デフォルト: `nothing`）凸包を計算するためのバックエンド（引数`apply_convex_hull`を参照）

### 出力

頂点のリスト、場合によっては凸包の頂点のリストに減少されることがあります。
