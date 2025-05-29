`reflection_subgroup(W::FiniteCoxeterGroup,I)`

`I⊆1:nref(W)` の場合、`refls(W,I)` によって生成される `W` の部分群 `H`。

[Deodhar1989](biblio.htm#Deo89) と [Dyer1990](biblio.htm#Dye90) によって独立に発見された定理は、反射によって生成されるコクセター系 `(W,S)` の部分群 `H` は、任意の `t'∈ Ref(H)` で `t` とは異なる場合に `length(W,tt')>length(W,t)` となる `t  ∈ Ref(H)` からなる標準的なコクセター生成集合を持つということです。これは `reflection_subgroup` によって `H` のコクセター系を決定するために使用されます。

```julia-repl
julia> W=coxgroup(:G,2)
G₂

julia> diagram(W)
O⇛ O G₂
1  2

julia> H=reflection_subgroup(W,[2,6])
G₂₍₂₆₎=Ã₁×A₁

julia> diagram(H)
O Ã₁
1
O A₁
2
```

`G₂₍₂₆₎` という表記は、`roots(W,[2,6])` が `H` の単純根の系であることを意味します。

`H` がコクセター群 `W` の標準的な放物部分群である場合、`H` に対する長さ関数（その生成元の集合に関して）は、`W` に対する長さ関数の制限です。これは、`W` の任意の反射部分群に対してはもはや真ではないかもしれません。

```julia-repl
julia> elH=word.(Ref(H),elements(H))
4-element Vector{Vector{Int64}}:
 []
 [1]
 [2]
 [1, 2]

julia> elW=word.(Ref(W),elements(H))
4-element Vector{Vector{Int64}}:
 []
 [2]
 [1, 2, 1, 2, 1]
 [1, 2, 1, 2, 1, 2]

julia> map(w->H(w...),elH)==map(w->W(w...),elW)
true
```

有限反射群を根の集合上の置換群として実装します。したがって、反射部分群 `H⊆ W` は置換部分群であり、その要素は親群の根の置換として表されます。
