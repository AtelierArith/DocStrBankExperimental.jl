`on_classes(G, aut)`

`aut` は群 `G` の自己同型です（置換群の場合、これは `G` を正規化する置換として与えられることがあります）。結果は、`aut` によって誘導される `1:nconjugacy_classes(G)` の置換です。

```julia-repl
julia> W=Group(Perm(1,2),Perm(2,3),Perm(4,5),Perm(5,6))
Group((1,2),(2,3),(4,5),(5,6))

julia> on_classes(W,Perm(1,4,2,5,3,6))
(2,4)(3,7)(6,8)
```
