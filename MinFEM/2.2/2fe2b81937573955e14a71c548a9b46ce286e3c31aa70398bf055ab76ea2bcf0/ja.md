```julia
mutable struct Mesh
```

体積と境界マーカーを持つ三角形有限要素メッシュの型。

# フィールド

  * `d::Int64`: 空間次元
  * `nnodes::Int64`: ノードの数
  * `nelems::Int64`: 要素の数
  * `nboundelems::Int64`: 物理的（マークされた）境界要素の数
  * `Nodes::Vector{Vector{Float64}}`: ノード座標のリスト
  * `Elements::Vector{Vector{Int64}}`: 要素ノードインデックスのリスト
  * `BoundaryElements::Vector{Vector{Int64}}`: 境界要素ノードインデックスのリスト
  * `ParentElements::Vector{Int64}`: 境界要素への親要素のリスト
  * `ParentBoundaries::Vector{Int64}`: 境界要素への親要素のローカル境界のリスト
  * `Boundaries::Dict{Int64, MinFEM.Boundary}`: マークされた境界の辞書
  * `Domains::Dict{Int64, MinFEM.Domain}`: マークされた体積領域の辞書
  * `Entities::Vector{Dict{Int64, MinFEM.Entity}}`: 物理エンティティの辞書
