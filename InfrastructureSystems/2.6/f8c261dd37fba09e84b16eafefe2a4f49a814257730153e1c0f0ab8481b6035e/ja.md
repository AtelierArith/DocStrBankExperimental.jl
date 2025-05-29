```julia
serialize(
    val::InfrastructureSystems.InfrastructureSystemsType
) -> Vector{Dict{String, Any}}

```

Juliaの値をJSONなどの非Julia形式に変換できる標準型にシリアライズします。valが構造体のインスタンスである場合は、Dictを返します。valがスカラー値である場合は、その値を返します。
