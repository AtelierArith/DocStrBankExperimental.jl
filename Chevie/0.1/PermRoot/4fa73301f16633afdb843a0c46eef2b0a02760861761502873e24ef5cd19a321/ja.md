`reflection_subgroup(W,r)`

は、複素反射群 `W` の反射部分群を返します。この部分群は `refls(W,r)` によって生成されます。

反射部分群 `H` は、`W` と同じ追加情報を持つ置換部分群であり、親 `W` との関係を表す新しい情報が追加されています：

`inclusion(H)`：`H` の根のインデックスが `W` の根の中での位置

`parent(H)`：`W` に設定されます。

`restriction(H)`：長さ `length(roots(W))` のリストで、`inclusion(H)` の位置に非ゼロのエントリがあり、`roots(H)` の各インデックスにバインドされています。

反射群が部分群でない場合でも、実際にはこの情報があり、トリビアルな値に設定されています：`inclusion(W)==restriction(W)==eachindex(roots(W))`、および `parent()==W`。これにより、親群または反射部分群のために多くのコードを同じ方法で記述することができます。

`reflection_subgroup(R)` は、`R` 自体が反射部分群である場合、`R` の親の反射部分群を返します。

```julia_repl
julia> W=coxgroup(:F,4)
F₄

julia> H=reflection_subgroup(W,[1,2,11,20])
F₄₍₉‚₂‚₁‚₁₆₎=D₄₍₃₂₁₄₎

julia> [restriction(H)]
1-element Vector{Vector{Int64}}:
 [1, 2, 0, 0, 5, 0, 0, 0, 3, 0  …  0, 16, 0, 19, 0, 21, 0, 22, 23, 24]

julia> reflection_subgroup(H,[1,2,3])
F₄₍₉₁₂₎=A₃₍₃₁₂₎Φ₁
```
