```
struct DecisionList{O} <: AbstractModel{O}
    rulebase::Vector{Rule{_O} where {_O<:O}}
    defaultconsequent::M where {M<:AbstractModel{<:O}}
    info::NamedTuple
end
```

`DecisionList`（または*決定テーブル*、または*ルールベースモデル*）は、IF-ELSEIF-ELSEブロックの意味を持つ象徴的モデルです：

```
IF (antecedent_1)     THEN (consequent_1)
ELSEIF (antecedent_2) THEN (consequent_2)
...
ELSEIF (antecedent_n) THEN (consequent_n)
ELSE (consequent_default) END
```

ここで、[`antecedent`](@ref)sは条件式であり、[`consequent`](@ref)sはブロックの実行可能なローカル結果です。

古典的な意味論を使用すると、[`antecedent`](@ref)sは順番に評価され、有効な前提が見つかるとすぐに[`consequent`](@ref)が返されるか、計算がELSE句に達するまで続きます。

また、[`AbstractModel`](@ref)、[`DecisionTree`](@ref)、[`Rule`](@ref)も参照してください。
