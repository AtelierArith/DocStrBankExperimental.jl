```
vertices_list(cha::ConvexHullArray; [apply_convex_hull]::Bool=true,
              [backend]=nothing, [prune]::Bool=apply_convex_hull)
```

有限個の集合の凸包の頂点のリストを返します。

### 入力

  * `cha`               – 有限個の集合の凸包
  * `apply_convex_hull` – （オプション、デフォルト: `true`）`true`の場合、凸包アルゴリズムを使用して頂点を後処理します
  * `backend`           – （オプション、デフォルト: `nothing`）凸包を計算するためのバックエンド（引数`apply_convex_hull`を参照）
  * `prune`             – （オプション、デフォルト: `apply_convex_hull`）`apply_convex_hull`のエイリアス

### 出力

頂点のリスト。
