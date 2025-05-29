`minima(P)` は `Poset` または `CPoset` の最小要素です。

`minima(P,E)` は `P` の要素の部分集合 `E` の最小要素です。

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
