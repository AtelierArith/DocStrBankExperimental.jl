```
struct MinBoundaryHighDegreeSelector <: AbstractVertexSelector
```

`MinBoundaryHighDegreeSelector`構造体は戦略を表します:     - 高*度*しきい値以上の次数を持つ頂点が存在する場合、それを選択し、そのk次数の隣接頂点を選択します。     - そうでない場合、隣接頂点のk層によってオープン頂点の最小数を持つ部分グラフを選択します。

# フィールド

  * `kb::Int`: 部分グラフを選択する際に考慮する隣接頂点の層の数。
  * `hd::Int`: 頂点が選択されるための次数のしきい値。
  * `kd::Int`: 部分グラフを選択する際に考慮する隣接頂点の層の数。
