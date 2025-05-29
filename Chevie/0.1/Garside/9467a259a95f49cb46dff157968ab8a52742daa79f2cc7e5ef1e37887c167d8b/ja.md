`centralizer_gens(b[,F];ss=Val(:sc))`

`b`の中心化生成元のリストです。この計算は、`b`のスライディング回路のカテゴリにおける自己準同型を計算することによって行われます。引数`ss`が与えられた場合、計算は対応するカテゴリで行われます – [`conjcat`](@ref)を参照してください。

引数`F`が与えられた場合、それは`b.M.W`に付随する反射コセットのフロベニウスのようなブレイドモノイドの自己同型である必要があります。そうすれば、`F`-中心化が計算されます。

```julia-repl
julia> W=coxgroup(:D,4)
D₄

julia> B=BraidMonoid(W)
BraidMonoid(D₄)

julia> w=B(4,4,4)
4.4.4

julia> cc=centralizer_gens(w)
8-element Vector{GarsideElt{Perm{Int16}, BraidMonoid{Perm{Int16}, FiniteCoxeterGroup{Perm{Int16},Int64}}}}:
 1
 (31432)⁻¹231432
 (1)⁻¹34.431
 (2)⁻¹34.432
 (32431)⁻¹132431
 4
 34.43
 2

julia> shrink(cc)
5-element Vector{GarsideElt{Perm{Int16}, BraidMonoid{Perm{Int16}, FiniteCoxeterGroup{Perm{Int16},Int64}}}}:
 4
 2
 1
 34.43
 (3243)⁻¹13243

julia> centralizer_gens(w;ss=Val(:cyc))
1-element Vector{GarsideElt{Perm{Int16}, BraidMonoid{Perm{Int16}, FiniteCoxeterGroup{Perm{Int16},Int64}}}}:
 4

julia> F=Frobenius(spets(W,Perm(1,2,4)));

julia> centralizer_gens(w,F)
2-element Vector{GarsideElt{Perm{Int16}, BraidMonoid{Perm{Int16}, FiniteCoxeterGroup{Perm{Int16},Int64}}}}:
 124
 312343123
```
