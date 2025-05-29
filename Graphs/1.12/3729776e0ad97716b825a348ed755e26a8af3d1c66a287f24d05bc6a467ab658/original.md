```
DFSIterator
```

`DFSIterator` is used to iterate through graph vertices using a depth-first search.  A source node(s) is optionally supplied as an `Int` or an array-like type that can be  indexed if supplying multiple sources.

# Examples

```julia-repl
julia> g = smallgraph(:house)
{5, 6} undirected simple Int64 graph

julia> for node in DFSIterator(g, 3)
           display(node)
       end
1
2
4
3
5
```
