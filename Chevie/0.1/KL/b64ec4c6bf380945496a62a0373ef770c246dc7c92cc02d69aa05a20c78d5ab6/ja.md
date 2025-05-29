`character(c)`

`c.group` の左セル `c` によって与えられる文字のリスト `l` を返します。これは `sum(CharTable(c.group).irr[l])` です。

```julia-repl
julia> c=left_cells(coxgroup(:G,2))[3]
LeftCell<G₂: duflo=2 character=φ₂‚₁+φ′₁‚₃+φ₂‚₂>

julia> character(c)
3-element Vector{Int64}:
 3
 5
 6
```
