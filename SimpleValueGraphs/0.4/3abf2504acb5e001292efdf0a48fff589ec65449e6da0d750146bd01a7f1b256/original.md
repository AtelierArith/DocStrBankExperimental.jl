```
ValEdge(s, d[, values])
ValEdge{V}(s, d[, values])
ValEdge{V, E_VALS}(s, d, values)
```

Create a `ValEdge` with source `s`, destination `d` and values `values`.

# Examples

```jldoctest
julia> e = ValEdge(1, 2, ('A',))
ValEdge 1 -- 2 with value A

julia> e = ValEdge(1, 2, ())
ValEdge 1 -- 2

julia> e = ValEdge(1,2, (first = 1, second = "2"))
ValEdge 1 -- 2 with values (first = 1, second = "2")
```
