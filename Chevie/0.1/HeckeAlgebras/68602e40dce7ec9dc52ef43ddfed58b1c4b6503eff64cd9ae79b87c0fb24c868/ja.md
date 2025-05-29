`char_values(h::HeckeTElt)`

`h` は Iwahori-Hecke 代数 `H` の要素です。この関数は `h` に対する `H` の不可約キャラクターの値を返します（使用される方法は `T` 基底に変換し、その後 `class_polynomials` を使用することです）。

```julia-repl
julia> W=coxgroup(:B,2)
B₂

julia> H=hecke(W,q^2;rootpara=q)
hecke(B₂,q²,rootpara=q)

julia> char_values(Cpbasis(H)(1,2,1))
5-element Vector{Pol{Int64}}:
 -q-q⁻¹
 q+q⁻¹
 0
 q³+2q+2q⁻¹+q⁻³
 0
```
