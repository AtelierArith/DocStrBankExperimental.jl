```
set_owns(
    r::RemoteConcept{<:AbstractType},
    attribute_type::AbstractType,
    is_key::Bool=false,
    overriden_type::Optional{AbstractType}=nothing
)
```

set_ownsを使用すると、属性を型に割り当てることができます。必要に応じて、属性をユニークとして設定することも可能です。これは、属性がキーとして設定されている型に対して、特定の属性を持つインスタンスは1つだけ存在できることを意味します。例えば、人物エンティティは属性としてユニークなメールアドレスを持っています。したがって、同じメールアドレスを持つ2つのエンティティを持つことはできません。
