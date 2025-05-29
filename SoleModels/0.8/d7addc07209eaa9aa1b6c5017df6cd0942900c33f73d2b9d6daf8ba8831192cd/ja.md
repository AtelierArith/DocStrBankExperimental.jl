```
struct DecisionList{O} <: AbstractModel{O}
    rulebase::Vector{Rule{_O} where {_O<:O}}
    defaultconsequent::M where {M<:AbstractModel{<:O}}
    info::NamedTuple
end
```

`DecisionList`（または*決定テーブル*、または*ルールベースモデル*）は、IF-ELSEIF-ELSEブロックの意味を持つ記号モデルです：

```
IF (antecedent_1)     THEN (consequent_1)
ELSEIF (antecedent_2) THEN (consequent_2)
...
ELSEIF (antecedent_n) THEN (consequent_n)
ELSE (consequent_default) END
```

ここで、前提は評価される式であり、結果はブロックの実行可能なローカル結果です。古典的な意味論を使用すると、前提は順番に評価され、有効な前提が見つかるとすぐに結果が返されるか、計算がELSE句に達するまで続きます。

[`Rule`](@ref)、[`DecisionTree`](@ref)、[`AbstractModel`](@ref)も参照してください。
