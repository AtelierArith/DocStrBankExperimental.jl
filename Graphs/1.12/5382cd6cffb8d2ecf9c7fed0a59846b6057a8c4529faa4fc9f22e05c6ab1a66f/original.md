```
BFSIterator(graph, source; depth_limit=nothing, neighbors_type=outneighbors)
```

`BFSIterator` is used to iterate through graph vertices using a breadth-first search. A source node(s) must be supplied as an `Int` or an array-like type that can be indexed if supplying multiple sources. It is also possible to specify a `depth_limit` which will stop the search once all nodes at that depth are visited and a `neighbors_type` which specifies what kind of neighbors of a node should be considered when exploring the graph.

# Examples

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
