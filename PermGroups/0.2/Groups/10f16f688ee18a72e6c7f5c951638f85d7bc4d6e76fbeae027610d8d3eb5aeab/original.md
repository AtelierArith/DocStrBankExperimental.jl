`center(G::Group)` the center of `G`

```julia-repl
julia> G=Group(Perm(1,2),Perm(3,4),Perm(1,3)*Perm(2,4))
Group((1,2),(3,4),(1,3)(2,4))

julia> center(G)
Group((1,2)(3,4))
```
