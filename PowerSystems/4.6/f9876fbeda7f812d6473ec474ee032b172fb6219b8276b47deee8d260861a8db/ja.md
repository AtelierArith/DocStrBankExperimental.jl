```julia
get_existing_device_types(
    sys::PowerSystems.System
) -> Vector{DataType}

```

システム内のすべてのデバイスタイプを返します。コンポーネントタイプやマスクされたコンポーネントは返しません。
