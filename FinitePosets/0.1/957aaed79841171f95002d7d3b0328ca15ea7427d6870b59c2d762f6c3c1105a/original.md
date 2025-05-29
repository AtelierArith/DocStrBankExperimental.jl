`maxima(P)` the maximal elements of the `Poset` or `CPoset`

`maxima(P,E)` the maximal elements of the subset `E` of elements of `P`

```julia-repl
julia> p=CPoset([[3],[3],[4,5],Int[],Int[]])
1,2<3<4,5

julia> maxima(p)
2-element Vector{Int64}:
 4
 5
 
julia> maxima(p,1:3)
1-element Vector{Int64}:
 3
```
