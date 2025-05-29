`on_classes(G, aut)`

`aut`  is an automorphism of  the group `G` (for  a permutation group, this could  be  given  as  a  permutation  normalizing  `G`).  The result is the permutation of `1:nconjugacy_classes(G)` induced by `aut`.

```julia-repl
julia> W=Group(Perm(1,2),Perm(2,3),Perm(4,5),Perm(5,6))
Group((1,2),(2,3),(4,5),(5,6))

julia> on_classes(W,Perm(1,4,2,5,3,6))
(2,4)(3,7)(6,8)
```
