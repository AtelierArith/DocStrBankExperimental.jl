```
ValDiEdge(s, d[, values])
ValDiEdge{V}(s, d[, values])
ValDiEdge{V, E_VALS}(s, d, values)
```

Create a `ValDiEdge` with source `s`, destination `d` and values `values`.

# Examples

```jldoctest
julia> e = ValDiEdge(1, 2, ('A',))
ValDiEdge 1 -> 2 with value A

julia> e = ValDiEdge(1, 2, ())
ValDiEdge 1 -> 2

julia> e = ValDiEdge(1,2, (first = 1, second = "2"))
ValDiEdge 1 -> 2 with values (first = 1, second = "2")
```
