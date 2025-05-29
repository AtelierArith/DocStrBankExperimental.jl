```
vidxs([inpr], components=:, variables=:) :: Vector{VIndex}
```

Generate vector of symbolic indexes for vertices.

  * `inpr`: Only needed for name matching or `:` access. Can be Network, sol, prob, ...
  * `components`: Number/Vector, `:`, `Symbol` (name matches), `String`/`Regex` (name contains)
  * `variables`: Symbol/Number/Vector, `:`, `String`/`Regex` (all sym containing)

Examples:

```
vidxs(nw)                 # all vertex state indices
vidxs(1:2, :u)            # [VIndex(1, :u), VIndex(2, :u)]
vidxs(nw, :, [:u, :v])    # [VIndex(i, :u), VIndex(i, :v) for i in 1:nv(nw)]
vidxs(nw, "ODEVertex", :) # all symbols of all vertices with name containing "ODEVertex"
```
