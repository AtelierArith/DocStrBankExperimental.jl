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

ここで、[`antecedent`](@ref)はチェックされるべき式であり、[`consequent`](@ref)sはブロックの実行可能なローカル結果です。前提条件のチェックが代数のトップに評価される場合、正の結果が適用されます。それ以外の場合は、負の結果が適用されます。

さらに、[`AbstractModel`](@ref)、[`antecedent`](@ref)、`SoleLogics.check`、`SoleLogics.Formula`、[`negconsequent`](@ref)、[`posconsequent`](@ref)、[`Rule`](@ref)も参照してください。
