```julia
DragScalarN(
    label,
    data_type::Union{CImGui.lib.ImGuiDataType_, Integer},
    p_data,
    components
) -> Bool
DragScalarN(
    label,
    data_type::Union{CImGui.lib.ImGuiDataType_, Integer},
    p_data,
    components,
    v_speed
) -> Bool
DragScalarN(
    label,
    data_type::Union{CImGui.lib.ImGuiDataType_, Integer},
    p_data,
    components,
    v_speed,
    p_min
) -> Bool
DragScalarN(
    label,
    data_type::Union{CImGui.lib.ImGuiDataType_, Integer},
    p_data,
    components,
    v_speed,
    p_min,
    p_max
) -> Bool
DragScalarN(
    label,
    data_type::Union{CImGui.lib.ImGuiDataType_, Integer},
    p_data,
    components,
    v_speed,
    p_min,
    p_max,
    format
) -> Bool
DragScalarN(
    label,
    data_type::Union{CImGui.lib.ImGuiDataType_, Integer},
    p_data,
    components,
    v_speed,
    p_min,
    p_max,
    format,
    flags::Union{CImGui.lib.ImGuiSliderFlags_, Integer}
) -> Bool

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L614).
