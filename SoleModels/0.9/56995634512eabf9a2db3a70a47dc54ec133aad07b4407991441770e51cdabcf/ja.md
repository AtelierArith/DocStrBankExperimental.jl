```
joinrules(rules::AbstractVector{<:Rule})::Vector{<:Rule}
```

入力されたルールのセットから、異なる結果ごとに正確に1つのルールを持つルールのセットを返します。各結果について、出力ルールはその結果に対する入力ルールの前提の論理和として計算されます。

# 例

```julia-repl
julia> using SoleLogics

julia> branch = Branch(SoleLogics.parseformula("p"), Branch(SoleLogics.parseformula("q"), "YES", "NO"), "NO")
 p
├✔ q
│├✔ YES
│└✘ NO
└✘ NO


julia> printmodel.(listrules(branch); tree_mode = true);
▣ p ∧ q
└✔ YES

▣ p ∧ ¬q
└✔ NO

▣ ¬p
└✔ NO

julia> printmodel.(joinrules(listrules(branch)); tree_mode = true);
▣ (p ∧ q)
└✔ YES

▣ (p ∧ ¬q) ∨ ¬p
└✔ NO

```

他の参照としては [`listrules`](@ref), [`SoleLogics.DISJUNCTION`](@ref), [`LeafModel`](@ref), [`AbstractModel`](@ref) があります。
