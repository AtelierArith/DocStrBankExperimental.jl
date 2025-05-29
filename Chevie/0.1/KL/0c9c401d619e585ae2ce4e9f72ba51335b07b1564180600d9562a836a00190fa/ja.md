`Lusztigaw(W,w)`

`w` がコクセター群 `W` の要素である場合、この関数は [5.10.2 Lusztig1985](biblio.htm#Lus85) で定義された仮想キャラクター `ca_w` の不可約キャラクターに対する係数を返します。このキャラクターは、対応するほぼキャラクターが整数であり、正であるという特性を持っています。

```julia-repl
julia> W=coxgroup(:G,2)
G₂

julia> l=Lusztigaw(W,W(1))
6-element Vector{Int64}:
 0
 0
 1
 0
 1
 1

julia> sum(l.*map(i->almostchar(W,i),eachindex(l)))
[G₂]:<φ′₁‚₃>+<φ₂‚₁>+<φ₂‚₂>
```
