```
disjunction(
    model::JuMP.AbstractModel, 
    disjunct_indicators::Vector{LogicalVariableRef},
    [nested_tag::Disjunct],
    [name::String = ""];
    [exactly1::Bool = true]
)
```

指標変数 `disjunct_indicators` を持つ不連続体から構成される不連続体を作成し、`model` に追加します。ネストされた不連続体の場合、`nested_tag` は親不連続体のどの不連続体に属するかを示すために必要です。デフォルトでは、`exactly1` は `@constraint(model, disjunct_indicators in Exactly(1))` の形の制約を追加し、選択できる不連続体は1つだけに制限されます。これは、[`Hull`](@ref) のような特定の再定式化に必要です。ネストされた不連続体の場合、`exactly1` は `@constraint(model, disjunct_indicators in Exactly(nested_tag.indicator))` の形の制約を作成します。多くの不連続体を一度に便利に生成するには、[`@disjunction`](@ref) と [`@disjunctions`](@ref) を参照してください。
