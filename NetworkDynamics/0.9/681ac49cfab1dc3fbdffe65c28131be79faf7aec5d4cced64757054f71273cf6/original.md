```
vidxs([inpr], components=:, variables=:) :: Vector{EIndex}
```

Generate vector of symbolic indexes for edges.

  * `inpr`: Only needed for name matching or `:` access. Can be Network, sol, prob, ...
  * `components`: Number/Vector, `:`, `Symbol` (name matches), `String`/`Regex` (name contains)
  * `variables`: Symbol/Number/Vector, `:`, `String`/`Regex` (all sym containing)

Examples:

```
eidxs(nw)                # all edge state indices
eidxs(1:2, :u)           # [EIndex(1, :u), EIndex(2, :u)]
eidxs(nw, :, [:u, :v])   # [EIndex(i, :u), EIndex(i, :v) for i in 1:ne(nw)]
eidxs(nw, "FlowEdge", :) # all symbols of all edges with name containing "FlowEdge"
```
