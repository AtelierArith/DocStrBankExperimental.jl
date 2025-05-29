```julia
struct CSPInstance{T, G<:Graphs.AbstractGraph{T}, FR, BR, C, FF<:(AbstractMatrix), BF<:(AbstractMatrix)} <: ConstrainedShortestPaths.AbstractCSPInstance
```

# フィールド

  * `graph::Graphs.AbstractGraph`: 最短経路を計算するための非循環有向グラフ
  * `origin_vertex::Any`: 経路の始点
  * `destination_vertex::Any`: 経路の終点
  * `origin_forward_resource::Any`: 始点での前方リソース
  * `destination_backward_resource::Any`: 終点での後方リソース
  * `cost_function::Any`: コスト関数
  * `forward_functions::AbstractMatrix`: 辺に沿った前方関数
  * `backward_functions::AbstractMatrix`: 辺に沿った後方関数
  * `is_useful::BitVector`: 経路計算において頂点が有用かどうかを示すビットベクタ、すなわち、始点から終点までの経路がそれを通るかどうか
  * `topological_ordering::Vector`: 有用な頂点の事前計算されたトポロジカル順序、終点から始点へ
