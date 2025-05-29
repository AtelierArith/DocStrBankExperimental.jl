```julia
TableSetupColumn(label)
TableSetupColumn(
    label,
    flags::Union{CImGui.lib.ImGuiTableColumnFlags_, Integer}
)
TableSetupColumn(
    label,
    flags::Union{CImGui.lib.ImGuiTableColumnFlags_, Integer},
    init_width_or_weight
)
TableSetupColumn(
    label,
    flags::Union{CImGui.lib.ImGuiTableColumnFlags_, Integer},
    init_width_or_weight,
    user_id::Integer
)

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L838).
