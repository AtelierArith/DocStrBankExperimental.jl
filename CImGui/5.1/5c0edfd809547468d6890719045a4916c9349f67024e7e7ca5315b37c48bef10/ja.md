```julia
MenuItem(
    label::Union{Ptr{Int8}, Ptr{Nothing}, String}
) -> Bool
MenuItem(
    label::Union{Ptr{Int8}, Ptr{Nothing}, String},
    shortcut::Union{Ptr{Int8}, Ptr{Nothing}, String}
) -> Bool
MenuItem(
    label::Union{Ptr{Int8}, Ptr{Nothing}, String},
    shortcut::Union{Ptr{Int8}, Ptr{Nothing}, String},
    selected::Bool
) -> Bool
MenuItem(
    label::Union{Ptr{Int8}, Ptr{Nothing}, String},
    shortcut::Union{Ptr{Int8}, Ptr{Nothing}, String},
    selected::Bool,
    enabled::Bool
) -> Bool

```

アクティブ化されたときにtrueを返します。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L741).
