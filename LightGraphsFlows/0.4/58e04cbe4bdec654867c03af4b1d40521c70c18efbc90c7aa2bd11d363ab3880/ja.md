```
maximum_flow(flow_graph, source, target[, capacity_matrix][, algorithm][, restriction])
```

`flow_graph`から`source`へ`target`までの一般的な最大*流関数で、`capacity_matrix`に容量があります。流れのアルゴリズム`algorithm`とカットオフ制限`restriction`を使用します。

  * `capacity_matrix`が指定されていない場合、`DefaultCapacity(flow_graph)`が使用されます。
  * `algorithm`が指定されていない場合、デフォルトで[`PushRelabelAlgorithm`](@ref)が使用されます。
  * `restriction`が指定されていない場合、デフォルトで`0`が使用されます。

(最大流、流行列)のタプルを返します。Boykov-Kolmogorovアルゴリズムの場合、関連する最小カットが3番目の出力として返されます。

### 使用例:

```julia
julia> flow_graph = lg.DiGraph(8) # フローグラフを作成
julia> flow_edges = [
(1,2,10),(1,3,5),(1,4,15),(2,3,4),(2,5,9),
(2,6,15),(3,4,4),(3,6,8),(4,7,16),(5,6,15),
(5,8,10),(6,7,15),(6,8,10),(7,3,6),(7,8,10)
]

julia> capacity_matrix = zeros(Int, 8, 8)  # 容量行列を作成

julia> for e in flow_edges
    u, v, f = e
    lg.add_edge!(flow_graph, u, v)
    capacity_matrix[u,v] = f
end

julia> f, F = maximum_flow(flow_graph, 1, 8) # 容量行列なしでデフォルトの最大流（プッシュ-リレーベル）を実行

julia> f, F = maximum_flow(flow_graph, 1, 8, capacity_matrix) # 容量行列を使用してデフォルトの最大流を実行

julia> f, F = maximum_flow(flow_graph, 1, 8, capacity_matrix, algorithm=EdmondsKarpAlgorithm()) # エドモンズ-カープアルゴリズムを実行

julia> f, F = maximum_flow(flow_graph, 1, 8, capacity_matrix, algorithm=DinicAlgorithm()) # ディニックのアルゴリズムを実行

julia> f, F, labels = maximum_flow(flow_graph, 1, 8, capacity_matrix, algorithm=BoykovKolmogorovAlgorithm()) # ボイコフ-コルモゴロフアルゴリズムを実行

```
