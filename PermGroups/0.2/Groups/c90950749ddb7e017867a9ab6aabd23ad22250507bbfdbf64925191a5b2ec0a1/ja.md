`transporting_elt(G,p,q,action=^)` または `transporting_element(G,p,q,action=^)`

は、`p^g==q` (または `action(p,g)==q` が指定されている場合は `action` を使用) を満たす `g∈ G` を返します。もしそのような `g` が存在しない場合は何も返しません。可能な `g` の集合は、G における p の中心化群の右コセットを形成します。

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
