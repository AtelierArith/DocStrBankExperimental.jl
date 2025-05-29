```
transitivereduction(g; selflooped=false)
```

有向グラフの推移的削減を計算します。グラフにサイクルが含まれている場合、各強連結成分は有向サイクルに置き換えられ、成分を接続する凝縮グラフ上で推移的削減が計算されます。`selflooped`がtrueの場合、サイズ1の強連結成分の自己ループは保持されます。

### パフォーマンス

時間計算量は$\mathcal{O}(|V||E|)$です。

# 例

```jldoctest
julia> using Graphs

julia> barbell = blockdiag(complete_digraph(3), complete_digraph(3));

julia> add_edge!(barbell, 1, 4);

julia> collect(edges(barbell))
13-element Vector{Graphs.SimpleGraphs.SimpleEdge{Int64}}:
 Edge 1 => 2
 Edge 1 => 3
 Edge 1 => 4
 Edge 2 => 1
 Edge 2 => 3
 Edge 3 => 1
 Edge 3 => 2
 Edge 4 => 5
 Edge 4 => 6
 Edge 5 => 4
 Edge 5 => 6
 Edge 6 => 4
 Edge 6 => 5

julia> collect(edges(transitivereduction(barbell)))
7-element Vector{Graphs.SimpleGraphs.SimpleEdge{Int64}}:
 Edge 1 => 2
 Edge 1 => 4
 Edge 2 => 3
 Edge 3 => 1
 Edge 4 => 5
 Edge 5 => 6
 Edge 6 => 4
```
