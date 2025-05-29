`with_inversions(W,N)`

`W`  should be  a finite  Coxeter group  and `N`  a subset  of `1:nref(W)`. Returns  the  element  `w`  of  `W` such that `N==inversions(W,w)`. Returns `nothing` if no such element exists.

```julia-repl
julia> W=coxgroup(:A,2)
A₂

julia> map(N->with_inversions(W,N),combinations(1:nref(W)))
8-element Vector{Union{Nothing, Perm{Int16}}}:
 ()
 (1,4)(2,3)(5,6)
 (1,3)(2,5)(4,6)
 nothing
 nothing
 (1,6,2)(3,5,4)
 (1,2,6)(3,4,5)
 (1,5)(2,4)(3,6)
```
