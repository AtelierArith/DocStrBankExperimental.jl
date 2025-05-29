```julia
agents_at(
    node,
    model::EasyABM.GraphModel{EasyABM.StaticType, T<:EasyABM.MType}
) -> Base.Generator{_A, F} where {_A, F<:(EasyABM.var"#543#544"{EasyABM.GraphModel{EasyABM.StaticType, T, G}} where {T<:EasyABM.MType, G<:EasyABM.GType})}

```

指定されたノードにいるエージェントのリストを返します。
