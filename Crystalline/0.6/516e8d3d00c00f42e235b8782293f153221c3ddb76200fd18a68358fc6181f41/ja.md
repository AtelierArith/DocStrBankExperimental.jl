```
conjugacy_relations(gr::GroupRelationGraph, sgnumᴳ, sgnumᴴ) --> Vector{<:ConjugacyTransform}
```

グラフ `gr` が部分群または超群の関係を表すとき、グループ `sgnumᴳ` と `sgnumᴴ` の間の共役類を構成する可能な変換を返します。

返される変換 `ts` は、`G` を `H` の設定に持ち込むもので、`transform.(G, Ref(t.P), Ref(t.p))` によって実行されます。ここで、`t` は `ts` の要素、すなわち一つの可能な共役変換であり、`t.P` と `t.p` は関連する変換の回転と平行移動をそれぞれ示します。

変換は体積を保持する必要はありません：したがって、変換後に冗長な操作があるかもしれません（[`reduce_ops`](@ref) または `unique!` を使用してこれらを削除してください）。

## 例

次の例では、空間群 ⋕168 と ⋕3 の間の部分群関係を考えます：

```jldoctest conjugacy_relation
julia> gr = maximal_subgroups(168)
GroupRelationGraph (subgroups) of SpaceGroup{3} ⋕168 with 4 vertices:
 ⋕168
 ├─►⋕143ᵀ (index 2)  ╌╌►⋕1ᵀ (index 3)
 └─►⋕3ᵀ (index 3)  ╌╌►⋕1ᵀ (index 2)

julia> sg168 = spacegroup(168)
SpaceGroup{3} ⋕168 (P6) with 6 operations:
 1
 3₀₀₁⁺
 3₀₀₁⁻
 2₀₀₁
 6₀₀₁⁻
 6₀₀₁⁺

julia> sg3 = spacegroup(3)
SpaceGroup{3} ⋕3 (P2) with 2 operations:
 1
 2₀₁₀
```

対称操作 2₀₁₀（⋕3 から）と 2₀₀₁（⋕168 から）は変換によって異なります；同型であるにもかかわらず、異なる設定にあるため、これは明確には反映されません。`conjugacy_relations` を使用して、⋕168 を ⋕3 の設定に持ち込む変換を見つけることができます：

```jldoctest conjugacy_relation
julia> ts = conjugacy_relations(gr, 168, 3) # ⋕168 から ⋕3 への可能な変換
1-element Vector{Crystalline.ConjugacyTransform{3}}:
 P = [0 0 1; 1 0 0; 0 1 0]

julia> sg168′ = transform.(sg168, Ref(ts[1].P), Ref(ts[1].p))
6-element Vector{SymOperation{3}}:
 1
 3₀₁₀⁺
 3₀₁₀⁻
 2₀₁₀
 6₀₁₀⁻
 6₀₁₀⁺

julia> issubgroup(sg168, sg3) # 設定が異なるため部分群として識別されない
false

julia> issubgroup(sg168′, sg3) # 設定が一致し、部分群関係が明らかになる
true
```

ここでは、可能な変換は1つだけですが、一般的には多くの変換が存在する可能性があります。
