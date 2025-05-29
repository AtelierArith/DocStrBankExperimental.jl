```julia
MenuItem(
    label::Union{Ptr{Int8}, Ptr{Nothing}, String},
    shortcut::Union{Ptr{Int8}, Ptr{Nothing}, String},
    p_selected::Ref{Bool}
) -> Bool
MenuItem(
    label::Union{Ptr{Int8}, Ptr{Nothing}, String},
    shortcut::Union{Ptr{Int8}, Ptr{Nothing}, String},
    p_selected::Ref{Bool},
    enabled::Bool
) -> Bool

```

アクティブ化されたときにtrueを返し、もしp*selected != NULLであればトグルします。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L742).
