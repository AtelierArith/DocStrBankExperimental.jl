`on_unipotents(W,aut)`

`W` は反射群または有限冗長群 $𝐆 ^F$ を表す反射コセットであり、`aut` は $𝐆 ^F$ の自己同型です（`W` が置換群の場合、これは根の置換として与えることができます）。この関数は、`aut` によって誘導される $𝐆 ^F$ のユニポテントキャラクターの置換を返します。これは特別な複素反射群に対して意味があり、それらに対して実装されています。

```julia-repl
julia> WF=rootdatum("3D4")
³D₄

julia> on_unipotents(Group(WF),WF.phi)
(1,7,2)(8,12,9)
```
