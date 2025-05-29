```julia
component_to_qualified_string(
    component_type::Type{<:InfrastructureSystems.InfrastructureSystemsComponent},
    component_name::AbstractString
) -> Any

```

`InfrastructureSystemsComponent`の仕様/インスタンスをシステムごとにユニークな文字列に変換する標準的な方法。
