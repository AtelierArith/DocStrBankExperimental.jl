```
get_has(transaction::AbstractCoreTransaction,
    thing::AbstractThing,
    attribute_type::Optional{AttributeType} = nothing,
    attribute_types::Optional{Vector{<:AbstractAttributeType}} = nothing,
    keys_only = false)
```

この関数を使用すると、エンティティまたはリレーションの属性を取得することができます。オプションとして、データベースから取得される属性の型を制限することができます。1つの型または複数の型のいずれかを選択できます。
