```julia
InputScalar(
    label,
    data_type::Union{CImGui.lib.ImGuiDataType_, Integer},
    p_data
) -> Bool
InputScalar(
    label,
    data_type::Union{CImGui.lib.ImGuiDataType_, Integer},
    p_data,
    p_step
) -> Bool
InputScalar(
    label,
    data_type::Union{CImGui.lib.ImGuiDataType_, Integer},
    p_data,
    p_step,
    p_step_fast
) -> Bool
InputScalar(
    label,
    data_type::Union{CImGui.lib.ImGuiDataType_, Integer},
    p_data,
    p_step,
    p_step_fast,
    format
) -> Bool
InputScalar(
    label,
    data_type::Union{CImGui.lib.ImGuiDataType_, Integer},
    p_data,
    p_step,
    p_step_fast,
    format,
    flags::Union{CImGui.lib.ImGuiInputTextFlags_, Integer}
) -> Bool

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L652).
