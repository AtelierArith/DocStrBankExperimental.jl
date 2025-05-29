```
ExclusiveTopology(grid::AbstractGrid)
```

**実験的機能** `ExclusiveTopology` は、グリッドのトポロジー（接続性/近傍）データを保存します。保存されるのは、最高次元の近傍のみです。つまり、何かが面と辺で接続されている場合、面の近傍のみが保存されます。低次元の近傍は、必要に応じて getneighborhood を呼び出すと再計算されます。

# フィールド

  * `vertex_to_cell::AbstractArray{AbstractVector{Int}, 1}`:           グローバル頂点IDからその頂点を含むすべてのセルへのマッピング
  * `cell_neighbor::AbstractArray{AbstractVector{Int}, 1}`:            セルIDからすべての接続されたセルへのマッピング
  * `face_neighbor::AbstractArray{AbstractVector{FaceIndex}, 2}`:      `face_neighbor[cellid,   local_face_id]`   -> 隣接する面
  * `edge_neighbor::AbstractArray{AbstractVector{EdgeIndex}, 2}`:      `edge_neighbor[cellid,   local_edge_id]`   -> 隣接する辺
  * `vertex_neighbor::AbstractArray{AbstractVector{VertexIndex}, 2}`:  `vertex_neighbor[cellid, local_vertex_id]` -> 隣接する頂点
  * `face_skeleton::Union{Vector{FaceIndex}, Nothing}`:     グリッド内のユニークな面のリスト（`FaceIndex`として）
  * `edge_skeleton::Union{Vector{EdgeIndex}, Nothing}`:     グリッド内のユニークな辺のリスト（`EdgeIndex`として）
  * `vertex_skeleton::Union{Vector{VertexIndex}, Nothing}`: グリッド内のユニークな頂点のリスト（`VertexIndex`として）

!!! warning "制限"
    実装は、適合するグリッド（「ハンギングノード」のないグリッド）でのみ機能します。非適合グリッドは予期しない結果をもたらします。埋め込まれたセル（空間次元に対して異なる参照次元を持つ）はサポートされておらず、構築時にエラーが発生します。

