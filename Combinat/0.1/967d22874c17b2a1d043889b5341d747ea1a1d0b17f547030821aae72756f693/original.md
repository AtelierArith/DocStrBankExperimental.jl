`robinson_schensted(p::AbstractVector{<:Integer})`

returns  the pair of standard tableaux  associated with the permutation `p` by the Robinson-Schensted correspondence.

```julia-repl
julia> robinson_schensted([2,3,4,1])
([[1, 3, 4], [2]], [[1, 2, 3], [4]])
```
