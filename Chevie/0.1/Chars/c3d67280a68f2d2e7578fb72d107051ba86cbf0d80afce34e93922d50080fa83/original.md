`on_chars(G,aut)`

`aut`  is an automorphism of  the group `G` (for  a permutation group, this could  be  given  as  a  permutation  normalizing  `G`).  The result is the permutation of the indices of the irreducible characters induced by `aut`.

```julia-repl
julia> WF=rootdatum("3D4")
³D₄

julia> on_chars(Group(WF),WF.phi)
(1,2,7)(8,9,12)
```
