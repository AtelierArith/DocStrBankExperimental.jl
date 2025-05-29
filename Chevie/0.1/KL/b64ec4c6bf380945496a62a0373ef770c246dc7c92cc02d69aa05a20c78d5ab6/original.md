`character(c)`

Returns  a list `l`  such that the  character of `c.group`  afforded by the left cell `c` is `sum(CharTable(c.group).irr[l])`.

```julia-repl
julia> c=left_cells(coxgroup(:G,2))[3]
LeftCell<G₂: duflo=2 character=φ₂‚₁+φ′₁‚₃+φ₂‚₂>

julia> character(c)
3-element Vector{Int64}:
 3
 5
 6
```
