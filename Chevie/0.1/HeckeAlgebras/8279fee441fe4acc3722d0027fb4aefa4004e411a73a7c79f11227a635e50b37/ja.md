`central_monomials(H)`

`H` を有限反射群 `W` のヘッケ代数とします。この関数は、`H` における `π` の像が `H` の不可約表現に作用するスカラーを返します。

`W` が不可約であるとき、`π` は純編組群の中心の生成元です。一般に、これは各不可約成分のそのような要素の積です。`W` がコクセター群であるとき、`H` における π の像は $T_{w_0}^2$ です。

```julia-repl
julia> H=hecke(coxgroup(:H,3),Pol(:q))
hecke(H₃,q)

julia> central_monomials(H)
10-element Vector{Pol{Cyc{Int64}}}:
 1
 q³⁰
 q¹²
 q¹⁸
 q¹⁰
 q¹⁰
 q²⁰
 q²⁰
 q¹⁵
 q¹⁵
```
