```
bridges(g)
```

接続されたグラフ `g` の[ブリッジ](https://en.wikipedia.org/wiki/Bridge_(graph_theory))を計算し、グラフの接続成分の数を増加させるエッジ、すなわち削除すると接続成分の数が増えるエッジを含む配列を返します。

# 例

```jldoctest
julia> using Graphs

julia> bridges(star_graph(5))
4-element Vector{Graphs.SimpleGraphs.SimpleEdge{Int64}}:
 Edge 1 => 2
 Edge 1 => 3
 Edge 1 => 4
 Edge 1 => 5

julia> bridges(path_graph(5))
4-element Vector{Graphs.SimpleGraphs.SimpleEdge{Int64}}:
 Edge 4 => 5
 Edge 3 => 4
 Edge 2 => 3
 Edge 1 => 2
```
