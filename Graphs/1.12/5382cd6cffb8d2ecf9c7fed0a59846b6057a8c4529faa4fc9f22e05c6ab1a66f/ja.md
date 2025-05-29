```
BFSIterator(graph, source; depth_limit=nothing, neighbors_type=outneighbors)
```

`BFSIterator`は、幅優先探索を使用してグラフの頂点を反復処理するために使用されます。ソースノードは、`Int`またはインデックス可能な配列型として提供する必要があります（複数のソースを提供する場合）。また、`depth_limit`を指定することも可能で、これによりその深さのすべてのノードが訪問されると探索が停止します。さらに、`neighbors_type`を指定することで、グラフを探索する際に考慮すべきノードの隣接ノードの種類を指定できます。

# 例

```julia-repl
julia> g = smallgraph(:house)
{5, 6} undirected simple Int64 graph

julia> for node in BFSIterator(g,3)
           display(node)
       end
3
1
4
5
2
```
