`SPerm{T}(l::AbstractVector,l1::AbstractVector)`

return  a `SPerm{T}` `p`  such that `invpermute(l1,p)==l`  if such `p` exists; returns  nothing otherwise.  If not  given `{T}`  is taken to be `{Int16}`. Needs the entries of `l` and `l1` to be sortable and have operation `-`.

```julia-repl
julia> p=SPerm([20,30,40],[-40,-20,-30])
(1,-3,2,-1,3,-2)

julia> invpermute([-40,-20,-30],p)
3-element Vector{Int64}:
 20
 30
 40
```
