`semisimple_centralizer_representatives(W [,p])` または `sscentralizer_reps`

`W` は代数群 `𝐆` に対応するウェイル群である必要があります。この関数は、半単純要素の中心化子の単位成分である `𝐆` の冗長部分群の `𝐆`-軌道の代表 `𝐇` を記述するリストを返します。各群 `𝐇` は、`W` の反射インデックスのリスト `h` によって指定され、`𝐇` は `reflection_subgroup(W,h)` に対応します。第二引数 `p` が与えられた場合、特性 `p` に現れる中心化子のリストのみが返されます。

```julia-repl
julia> W=coxgroup(:G,2)
G₂

julia> sscentralizer_reps(W)
6-element Vector{Vector{Int64}}:
 []
 [1]
 [2]
 [1, 2]
 [1, 5]
 [2, 6]

julia> reflection_subgroup.(Ref(W),sscentralizer_reps(W))
6-element Vector{FiniteCoxeterSubGroup{Perm{Int16},Int64}}:
 G₂₍₎=Φ₁²
 G₂₍₁₎=A₁Φ₁
 G₂₍₂₎=Ã₁Φ₁
 G₂
 G₂₍₁₅₎=A₂
 G₂₍₂₆₎=Ã₁×A₁

julia> sscentralizer_reps(W,2)
5-element Vector{Vector{Int64}}:
 []
 [1]
 [2]
 [1, 2]
 [1, 5]
```
