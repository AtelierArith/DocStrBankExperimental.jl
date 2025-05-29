```
vertices_list(ch::ConvexHull; [apply_convex_hull]::Bool=true,
              [backend]=nothing)
```

2つの集合の凸包の頂点のリストを返します。

### 入力

  * `ch`                – 2つの集合の凸包
  * `apply_convex_hull` – （オプション、デフォルト: `true`）`true`の場合、凸包アルゴリズムを使用して頂点を後処理します
  * `backend`           – （オプション、デフォルト: `nothing`）凸包を計算するためのバックエンド（引数 `apply_convex_hull` を参照）

### 出力

頂点のリスト。
