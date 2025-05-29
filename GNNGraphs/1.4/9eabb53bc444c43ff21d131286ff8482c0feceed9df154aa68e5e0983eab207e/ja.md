```
to_bidirected(g)
```

グラフ内の各エッジに対して逆エッジを追加し、その後、グラフを簡略化するために `mean` 集約を使用して [`remove_multi_edges`](@ref) を呼び出します。

関連情報として [`is_bidirected`](@ref) も参照してください。

# 例

```jldoctest
julia> s, t = [1, 2, 3, 3, 4], [2, 3, 4, 4, 4];

julia> w = [1.0, 2.0, 3.0, 4.0, 5.0];

julia> e = [10.0, 20.0, 30.0, 40.0, 50.0];

julia> g = GNNGraph(s, t, w, edata = e)
GNNGraph:
  num_nodes: 4
  num_edges: 5
  edata:
    e = 5-element Vector{Float64}

julia> g2 = to_bidirected(g)
GNNGraph:
  num_nodes: 4
  num_edges: 7
  edata:
    e = 7-element Vector{Float64}

julia> edge_index(g2)
([1, 2, 2, 3, 3, 4, 4], [2, 1, 3, 2, 4, 3, 4])

julia> get_edge_weight(g2)
7-element Vector{Float64}:
 1.0
 1.0
 2.0
 2.0
 3.5
 3.5
 5.0

julia> g2.edata.e
7-element Vector{Float64}:
 10.0
 10.0
 20.0
 20.0
 35.0
 35.0
 50.0
```
