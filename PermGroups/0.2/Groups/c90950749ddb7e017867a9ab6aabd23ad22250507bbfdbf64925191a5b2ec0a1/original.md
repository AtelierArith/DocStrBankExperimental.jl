`transporting_elt(G,p,q,action=^)`    or `transporting_element(G,p,q,action=^)`

returns  an  element  `g∈  G`  such  that  `p^g==q` (or `action(p,g)==q` if `action` is given), if such a `g` exists, and nothing otherwise. The set of possible `g` forms a right coset of the centralizer of p in G.

```julia-repl
julia> g=Group(perm"(1,2,3)(6,7)",perm"(3,4,5)(7,8)")
Group((1,2,3)(6,7),(3,4,5)(7,8))

julia> transporting_elt(g,1,5)
(1,5,4,3,2)

julia> transporting_elt(g,1,6)

julia> transporting_elt(g,[1,2,3,4],[2,3,4,5],(s,g)->sort(s.^g))
(1,2,3,4,5)(6,7,8)

julia> transporting_elt(g,[1,2,3,4],[3,4,5,2],(s,g)->s.^g)
```
