```julia
InputScalarN(
    label,
    data_type::Union{CImGui.lib.ImGuiDataType_, Integer},
    p_data,
    components
) -> Bool
InputScalarN(
    label,
    data_type::Union{CImGui.lib.ImGuiDataType_, Integer},
    p_data,
    components,
    p_step
) -> Bool
InputScalarN(
    label,
    data_type::Union{CImGui.lib.ImGuiDataType_, Integer},
    p_data,
    components,
    p_step,
    p_step_fast
) -> Bool
InputScalarN(
    label,
    data_type::Union{CImGui.lib.ImGuiDataType_, Integer},
    p_data,
    components,
    p_step,
    p_step_fast,
    format
) -> Bool
InputScalarN(
    label,
    data_type::Union{CImGui.lib.ImGuiDataType_, Integer},
    p_data,
    components,
    p_step,
    p_step_fast,
    format,
    flags::Union{CImGui.lib.ImGuiInputTextFlags_, Integer}
) -> Bool

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L653).
