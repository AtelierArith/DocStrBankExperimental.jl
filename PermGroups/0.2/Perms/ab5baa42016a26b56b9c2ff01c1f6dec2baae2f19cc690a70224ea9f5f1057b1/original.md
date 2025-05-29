`Perm{T}(l::AbstractVector,l1::AbstractVector)`

returns  `p`, a  `Perm{T}`, such  that `invpermute(l1,p)==l`  if such a `p` exists;  returns `nothing`  otherwise. If  not given  `{T}` is  taken to be `{Int16}`. Needs the `eltype` of `l` and `l1` to be sortable.

```julia-repl
julia> Perm([0,2,4],[4,0,2])
(1,3,2)
```
