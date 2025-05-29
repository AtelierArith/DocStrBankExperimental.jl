`twistings(W,I)`

`W` は複素反射群である必要があります。

この関数は、`W`-共役に関しての `W` の部分集合のリストを返します。その群は `reflection_subgroup(W,I)` です。ウェイル群の場合、これは `reflection_subgroup(W,I)` に対応する最大ランク `L` の冗長部分群の可能なねじれた形の代表に相当します。これらは `N_W(L)/L` のクラスによって分類されます。

`W` はコセット `Wϕ` であることもできます。その場合、部分群 `L` は有理形が存在するために `ϕ(L)` に共役でなければなりません。もし `wϕ` が `L` を正規化するなら、冗長形は `N_W(L)/L` の `wϕ`-クラスによって分類されます。

```julia-repl
julia> W=coxgroup(:E,6)
E₆

julia> WF=spets(W,Perm(1,6)*Perm(3,5))
²E₆

julia> twistings(W,2:5)
3-element Vector{Spets{FiniteCoxeterSubGroup{Perm{Int16},Int64}}}:
 E₆₍₂₃₄₅₎=D₄Φ₁²
 E₆₍₂₃₄₅₎=³D₄Φ₃
 E₆₍₂₃₄₅₎=²D₄Φ₁Φ₂


julia> twistings(WF,2:5)
3-element Vector{Spets{FiniteCoxeterSubGroup{Perm{Int16},Int64}}}:
 ²E₆₍₂₃₄₅₎=²D₄₍₁₄₃₂₎Φ₁Φ₂
 ²E₆₍₂₃₄₅₎=³D₄₍₁₄₃₂₎Φ₆
 ²E₆₍₂₃₄₅₎=D₄Φ₂²
```
