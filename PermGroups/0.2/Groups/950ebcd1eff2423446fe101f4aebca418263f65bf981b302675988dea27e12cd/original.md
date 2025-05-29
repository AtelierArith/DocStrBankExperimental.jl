`centralizer(G::Group,p,action=^)`

computes  the subgroup of elements `g` of `G` such that `action(p,g)==p`.

```julia-repl
julia> G=Group(Perm(1,2),Perm(1,2,3));
julia> centralizer(G,1)
Group((2,3))
```
