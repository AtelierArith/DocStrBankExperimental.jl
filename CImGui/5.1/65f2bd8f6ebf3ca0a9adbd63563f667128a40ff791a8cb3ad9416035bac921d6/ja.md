```julia
Begin(name::Union{Ptr{Int8}, Ptr{Nothing}, String}) -> Bool
Begin(
    name::Union{Ptr{Int8}, Ptr{Nothing}, String},
    p_open
) -> Bool
Begin(
    name::Union{Ptr{Int8}, Ptr{Nothing}, String},
    p_open,
    flags::Union{CImGui.lib.ImGuiWindowFlags_, Integer}
) -> Bool

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L377).
