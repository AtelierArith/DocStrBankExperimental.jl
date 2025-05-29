```
listrules(
    m::AbstractModel;
    use_shortforms::Bool = true,
    use_leftmostlinearform::Union{Nothing,Bool} = nothing,
    normalize::Bool = false,
    force_syntaxtree::Bool = false,
)::Vector{<:Rule}
```

シンボリックモデルに封じ込められた知識を捉えるルールのリストを返します。任意のシンボリックモデルの振る舞いは、相互に排他的（およびモデルが閉じている場合は共同で網羅的）なルールのセットとして合成され、表現することができ、これは多くの目的に役立ちます。

キーワード引数 `force_syntaxtree` を true に設定すると、返されるルールの論理的前提が他の構文構造（例：`LeftmostConjunctiveForm`）ではなく `SyntaxTree` として表現されるようになります。

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

```

他にも [`listimmediaterules`](@ref), [`SoleLogics.CONJUNCTION`](@ref), [`joinrules`](@ref), [`LeafModel`](@ref), [`AbstractModel`](@ref) を参照してください。
