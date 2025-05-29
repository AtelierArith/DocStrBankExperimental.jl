`(G::Group)(i...)`

A Group used as a function takes integer arguments in `eachindex(gens(W))`. This  constructs  the  element  of  `G`  product of the generators with the specified  indices. An argument  can also be  negative, then the inverse of the corresponding generator is used.

```julia-repl
julia> G=Group(Perm(1,2),Perm(1,2,3))
Group((1,2),(1,2,3))

julia> G(2,1,-2) # returns gens(G)[2]*gens(G)[1]/gens(G)[2]
(1,3)
```
