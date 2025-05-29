```
DataDiGraph{T,VL,VD,ED,GD} <: AbstractDataGraph{T}
```

隣接リストストレージに基づくメタデータを持つグラフの構造。

# フィールド

  * `ne::Int`: エッジの数
  * `fadjlist::Vector{Vector{Int}}`: 前方隣接リスト
  * `badjlist::Vector{Vector{Int}}`: 後方隣接リスト
  * `labels::Vector{VL}`: 頂点ラベルのリスト
  * `vertices::Dict{VL,T}`: 各頂点ラベルを関連付けられた整数インデックス `v` にマッピングする辞書
  * `vertex_data::Vector{VD}`: 整数 `v` によってインデックス付けされた頂点データオブジェクトのリスト
  * `edge_data::Vector{Vector{ED}}`: 最初に `s`、次に `d_index` でインデックス付けされたエッジデータオブジェクトのリスト。ここで `d_index` は `s` の外部隣接点の中での `d` のランク
  * `graph_data::GD`: 単一のグラフデータオブジェクト
