OpenStreetMapノード、ウェイ、リレーションおよびグラフ関連オブジェクトを格納するためのコンテナ。

# フィールド

`U <: Integer,T <: Union{String, Int},W <: Real`

  * `nodes::Dict{T,Node{T}}`: ノードIDをノードオブジェクトにマッピングします。
  * `node_coordinates::Vector{Vector{W}}`: ノードの座標のベクター [[lat, lon]...], グラフの頂点によってインデックス付けされています。
  * `ways::Dict{T,Way{T}}`: ウェイIDをウェイオブジェクトにマッピングします。以前は `highways` と呼ばれていました。
  * `node_to_index::OrderedDict{T,U}`: ノードIDをグラフの頂点にマッピングします。
  * `index_to_node::OrderedDict{U,T}`: グラフの頂点をノードIDにマッピングします。
  * `node_to_way::Dict{T,Vector{T}}`: ノードIDをウェイIDのベクターにマッピングします。以前は `node_to_highway` と呼ばれていました。
  * `edge_to_way::Dict{Vector{T},T}`: エッジ（隣接ノードペア）をウェイIDにマッピングします。以前は `edge_to_highway` と呼ばれていました。
  * `restrictions::Dict{T,Restriction{T}}`: リレーションIDを制限オブジェクトにマッピングします。
  * `indexed_restrictions::Union{DefaultDict{U,Vector{MutableLinkedList{U}}},Nothing}`: 通過ノードIDを制限されたノードIDの順序付きシーケンスにマッピングします。
  * `graph::Union{AbstractGraph,Nothing}`: DiGraph、StaticDiGraph、SimpleWeightedDiGraphまたはMetaDiGraphのいずれかです。
  * `weights::Union{SparseMatrixCSC{W,U},Nothing}`: スパース隣接行列（グラフの頂点間の重み）、`:distance`（km）、`:time`（時間）または`:lane_efficiency`（レーン数でスケーリングされた時間）のいずれかです。
  * `dijkstra_states::Vector{Vector{U}}`: ソース頂点によってインデックス付けされたダイクストラ親状態のベクターで、ソース頂点から他の任意の頂点への最短経路を取得するために使用されます。
  * `kdtree::Union{KDTree,Nothing}`: 最近接ノードを計算するために使用されるKDTreeです。
  * `kdtree::Union{RTree,Nothing}`: 最近接ノードを計算するために使用されるR-treeです。
  * `weight_type::Union{Symbol,Nothing}`: `:distance`、`:time`または`:lane_efficiency`のいずれかです。
