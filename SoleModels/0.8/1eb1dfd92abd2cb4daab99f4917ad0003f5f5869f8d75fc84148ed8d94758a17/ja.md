```
listimmediaterules(m::AbstractModel{O} where {O})::Rule{<:O}
```

シンボリックモデルに相当する即時ルールをリストします。

# 例

```julia-repl
julia> using SoleLogics

julia> branch = Branch(SoleLogics.parseformula("p"), Branch(SoleLogics.parseformula("q"), "YES", "NO"), "NO")
 p
├✔ q
│├✔ YES
│└✘ NO
└✘ NO


julia> printmodel.(listimmediaterules(branch); tree_mode = true);
▣ p
└✔ q
 ├✔ YES
 └✘ NO

▣ ¬(p)
└✔ NO


```

参照してください [`listrules`](@ref), [`AbstractModel`](@ref).
