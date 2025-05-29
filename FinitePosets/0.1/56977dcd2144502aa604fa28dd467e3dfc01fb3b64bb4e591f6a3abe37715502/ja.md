`antichains(p::CPoset)` は `p` の反鎖を計算します。

```julia-repl
julia> p=CPoset((i,j)->j%i==0,4)
1<3
1<2<4

julia> FinitePosets.antichains(p)
7-element Vector{Vector{Int64}}:
 []
 [1]
 [2]
 [3]
 [4]
 [2, 3]
 [3, 4]
```
