`FamiliesClassical(l)`

`l`  should be a list of symbols which classify the unipotent characters of a  classical reductive group, like `symbols(2,r)` for type `Bᵣ` or `Cᵣ`, or `symbols(2,r,0)`  for type `Dᵣ`. The function  returns the list of families determined  by these symbols.

```julia-repl
julia> FamiliesClassical(symbols(2,3)) # for a reductive group of type B₃
6-element Vector{Family}:
 Family(112,[2])
 Family(022,[6])
 Family(3,[9])
 Family(01123,[1, 3, 8, 11])
 Family(0112233,[4])
 Family(013,[5, 7, 10, 12])
```
