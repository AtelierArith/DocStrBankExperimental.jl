```
struct Branch{O} <: AbstractModel{O}
    antecedent::Formula
    posconsequent::M where {M<:AbstractModel{<:O}}
    negconsequent::M where {M<:AbstractModel{<:O}}
    info::NamedTuple
end
```

`Branch`はシンボリックモデリングの基本的な構成要素の一つであり、意味は次の通りです：

```
IF (antecedent) THEN (positive consequent) ELSE (negative consequent) END
```

ここで、antecedentはチェックされるべき式であり、consequentはブロックの実行可能なローカル結果です。antecedentのチェックが代数のトップに評価される場合、positive consequentが適用されます。そうでない場合、negative consequentが適用されます。

また、[`antecedent`](@ref)、[`posconsequent`](@ref)、[`negconsequent`](@ref)、[`SoleLogics.check`](@ref)、[`SoleLogics.Formula`](@ref)、[`Rule`](@ref)、[`AbstractModel`](@ref)も参照してください。
