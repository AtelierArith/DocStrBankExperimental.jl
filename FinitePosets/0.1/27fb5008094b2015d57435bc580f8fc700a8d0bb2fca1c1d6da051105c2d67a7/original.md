`minima(P)` the minimal elements of the `Poset` or `CPoset`

`minima(P,E)` the minimal elements of the subset `E` of elements of `P`

```julia-repl
julia> p=CPoset([[3],[3],[4,5],Int[],Int[]])
1,2<3<4,5

julia> minima(p)
2-element Vector{Int64}:
 1
 2
 
julia> minima(p,3:5)
1-element Vector{Int64}:
 3
```
