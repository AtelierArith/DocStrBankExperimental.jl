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

ここで、antecedentはチェックされるべき式であり、consequentはブロックのローカルな結果です。

[`antecedent`](@ref)、[`consequent`](@ref)、[`SoleLogics.Formula`](@ref)、[`AbstractModel`](@ref)も参照してください。
