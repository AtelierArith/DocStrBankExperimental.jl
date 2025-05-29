`on_chars(G,aut)`

`aut` は群 `G` の自己同型です（置換群の場合、これは `G` を正規化する置換として与えられることがあります）。結果は、`aut` によって誘導される不可約キャラクターのインデックスの置換です。

```julia-repl
julia> WF=rootdatum("3D4")
³D₄

julia> on_chars(Group(WF),WF.phi)
(1,2,7)(8,9,12)
```
