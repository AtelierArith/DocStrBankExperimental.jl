`maxima(P)` は `Poset` または `CPoset` の最大要素を返します。

`maxima(P,E)` は `P` の要素の部分集合 `E` の最大要素を返します。

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
