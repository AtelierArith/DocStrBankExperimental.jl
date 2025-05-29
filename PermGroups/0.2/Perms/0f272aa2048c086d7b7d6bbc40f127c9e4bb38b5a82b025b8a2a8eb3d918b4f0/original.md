`invpermute(l::AbstractVector,p::Perm)`

returns  `l` invpermuted by  `p`, a vector  `r` of same  length as `l` such that `r[i^p]==l[i]` for `i` in `eachindex(l)`. This function corresponds to the  GAP function  `Permuted`, but  we changed  the name  to fit  the Julia conventions since `invpermute(l,p)==invpermute!(copy(l),perm(p))`.

```julia-repl
julia> invpermute([5,4,6],Perm(1,2,3))
3-element Vector{Int64}:
 6
 5
 4
```
