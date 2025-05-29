```julia
BeginTable(str_id, columns) -> Bool
BeginTable(
    str_id,
    columns,
    flags::Union{CImGui.lib.ImGuiTableFlags_, Integer}
) -> Bool
BeginTable(
    str_id,
    columns,
    flags::Union{CImGui.lib.ImGuiTableFlags_, Integer},
    outer_size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
) -> Bool
BeginTable(
    str_id,
    columns,
    flags::Union{CImGui.lib.ImGuiTableFlags_, Integer},
    outer_size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    inner_width
) -> Bool

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L824).
