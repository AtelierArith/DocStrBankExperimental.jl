```julia
struct UnitDiskGraph{D, T} <: Graphs.AbstractGraph{Int64}
```

単位円グラフは、頂点が平面上の点であり、2つの頂点がエッジで接続されるのは、彼らの間のユークリッド距離が与えられた半径以下である場合のみです。

### フィールド

  * `locations::Vector{NTuple{D, T}}`: 頂点の位置
  * `radius::Float64`: 単位円の半径
