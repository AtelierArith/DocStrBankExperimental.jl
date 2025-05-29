`centralizer(G::Group,H::Group)` the centralizer in `G` of the group `H`

```julia-repl
julia> G=Group(Perm(1,2),Perm(1,2,3))
Group((1,2),(1,2,3))

julia> centralizer(G,Group(Perm(1,2)))
Group((1,2))
```
