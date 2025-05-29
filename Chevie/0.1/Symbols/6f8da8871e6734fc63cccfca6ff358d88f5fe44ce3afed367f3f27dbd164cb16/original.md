`symbols(e,r,c=1,def=0)` 

The list of `e`-symbols of rank `r`, content `c` and Malle-defect `def`

An `e`-symbol is a symbol of length `e`. The content of an `e`-symbol `S` is `sum(length,S)%e`. The symbols for unipotent  characters of:

  * `G(d,1,r)` are `symbols(d,r)`
  * `G(e,e,r)` are `symbols(e,r,0)`.
  * `G(e,e,r).s₁ᵗ` where `s₁` is the first generator of `G(e,1,r)` and `t|e` are `symbols(e,r,0,t)`

```julia-repl
julia> stringsymbol.(symbols(3,2)) # unipotent characters of G(3,1,2)
14-element Vector{String}:
 "(12,0,0)"
 "(02,1,0)"
 "(02,0,1)"
 "(012,12,01)"
 "(01,1,1)"
 "(012,01,12)"
 "(2,,)"
 "(01,2,0)"
 "(01,0,2)"
 "(1,012,012)"
 "(,02,01)"
 "(,01,02)"
 "(0,,012)"
 "(0,012,)"

julia> stringsymbol.(symbols(3,3,0)) # unipotent characters of G(3,3,3)
12-element Vector{String}:
 "(1+)"
 "(1E(3))"
 "(1E(3,2))"
 "(01,12,02)"
 "(01,02,12)"
 "(012,012,123)"
 "(0,1,2)"
 "(0,2,1)"
 "(01,01,13)"
 "(0,0,3)"
 "(012,,)"
 "(012,012,)"
```
