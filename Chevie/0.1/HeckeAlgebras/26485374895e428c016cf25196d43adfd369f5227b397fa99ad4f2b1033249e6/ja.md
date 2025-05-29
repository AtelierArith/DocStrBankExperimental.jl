`isrepresentation(H::HeckeAlgebra,r)`

は、与えられた要素の集合 `r` が反射群 `H.W` の標準生成子に対応するかどうかに応じて、与えられたヘッケ代数 `H` の表現を定義するかどうかを示す `true` または `false` を返します。

```julia-repl
julia> H=hecke(coxgroup(:F,4))
hecke(F₄,1)

julia> isrepresentation(H,reflrep(H))
true

julia> isrepresentation(H,Tbasis(H).(1:4))
true
```
