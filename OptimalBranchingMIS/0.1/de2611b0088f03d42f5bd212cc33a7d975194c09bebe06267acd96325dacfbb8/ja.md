```
struct MinBoundarySelector <: AbstractSelector
```

`MinBoundarySelector`構造体は、隣接するk層の頂点によってオープン頂点の最小数を持つ部分グラフを選択するための戦略を表します。

# フィールド

  * `k::Int`: 部分グラフを選択する際に考慮する隣接層の数。
