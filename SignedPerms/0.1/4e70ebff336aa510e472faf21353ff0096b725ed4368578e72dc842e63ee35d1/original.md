`invpermute(l::AbstractVector,p::SPerm)`

returns `l` invpermuted by `p`, a vector `r` such that `r[abs(i^p)]=l[i]*sign(i^p)`.

```julia-repl
julia> p=SPerm([-2,-1,-3])
SPerm{Int64}: (1,-2)(3,-3)

julia> invpermute([20,30,40],p)
3-element Vector{Int64}:
 -30
 -20
 -40
```

`invpermute` can also act on matrices with a keyword `dims`. If `dims=1` it invpermutes  the lines, if `dims=2` the  columns and for `dims=(1,2)` both. If `P=Matrix(p)` and `iP=Matrix(inv(p))` then `invpermute(m,p;dims=1)==iP*m`,      `invpermute(m,p;dims=2)==m*P`      and `invpermute(m,p;dims=(1,2))==iP*m*P`. Finally, the form `invpermute(m,p1,p2)`  invpermutes the lines of `m` by `p1` and the columns by `p2`.
