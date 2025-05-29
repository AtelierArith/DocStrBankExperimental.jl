```julia
get_existing_component_types(
    sys::PowerSystems.System
) -> Vector{DataType}

```

システム内のすべてのコンポーネントタイプを返します。マスクされたコンポーネントは返しません。
