`chainspoly(P)` は `Poset` または `CPoset` のチェーン多項式であり、その係数のリストとして返されます。

```julia-repl
julia> chainpoly(Poset(:powerset,3))
5-element Vector{Int64}:
  1
  8
 19
 18
  6
```
