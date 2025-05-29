`stabilizer(G::Group,s,action=^)`

computes  the subgroup of elements `g` of `G` such that `action(p,g)==p`.

```julia-repl
julia> G=Group(Perm(1,2),Perm(1,2,3,4))
Group((1,2),(1,2,3,4))
```

Assume that `s` is a set, represented as a sorted list without repetitions. `onsets` is the  action  of  `g∈  G`  given  by  `(g,p)->sort(p.^g)`.

```julia-repl
julia> stabilizer(G,[1,2],onsets)
Group((3,4),(1,2))
```
