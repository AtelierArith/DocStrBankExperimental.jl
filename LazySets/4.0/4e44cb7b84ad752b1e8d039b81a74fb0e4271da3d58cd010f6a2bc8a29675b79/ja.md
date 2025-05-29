```
minkowski_sum(P::LazySet, Q::LazySet;
              [backend]=nothing, [algorithm]=nothing, [prune]=true)
```

2つの多面体集合のミンコフスキー和を計算します。

### 入力

  * `P`         – 多面体集合
  * `Q`         – 多面体集合
  * `backend`   – （オプション、デフォルト: `nothing`）多面体計算バックエンド
  * `algorithm` – （オプション、デフォルト: `nothing`）変数を排除するためのアルゴリズム；利用可能なオプションは `Polyhedra.FourierMotzkin`、`Polyhedra.BlockElimination`、および `Polyhedra.ProjectGenerators`
  * `prune`     – （オプション、デフォルト: `true`）`true`の場合、冗長な制約や頂点を削除するための後処理を適用

### 出力

2次元の場合、集合が多角形であれば、結果は `VPolygon` になります。次元が高い場合、`P` と `Q` の両方がその型によって有界であることが知られていれば、結果は `HPolytope` になり、そうでなければ `HPolyhedron` になります。

### 注意事項

このメソッドは、両方の集合 `P` と `Q` の制約のリストを取得できる必要があります。それぞれの制約のリストを取得した後、多面体集合のための `minkowski_sum` メソッドが使用されます。
