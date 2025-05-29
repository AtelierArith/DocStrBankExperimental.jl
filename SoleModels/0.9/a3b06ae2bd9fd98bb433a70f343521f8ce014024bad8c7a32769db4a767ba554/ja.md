```
struct Rule{O} <: AbstractModel{O}
    antecedent::Formula
    consequent::M where {M<:AbstractModel{<:O}}
    info::NamedTuple
end
```

`Rule`はシンボリックモデリングの基本的な構成要素の一つであり、意味は次の通りです：

```
IF (antecedent) THEN (consequent) END
```

ここで、[`antecedent`](@ref)はチェックされるべき式であり、[`consequent`](@ref)はブロックのローカルな結果です。

# 例

```julia-repl
julia> Rule(CONJUNCTION(Atom("p"), Atom("q")), ConstantModel(2))
▣ (p) ∧ (q)  ↣  2
```

さらに詳しくは、[`AbstractModel`](@ref)、[`antecedent`](@ref)、[`consequent`](@ref)、`SoleLogics.Formula`を参照してください。
