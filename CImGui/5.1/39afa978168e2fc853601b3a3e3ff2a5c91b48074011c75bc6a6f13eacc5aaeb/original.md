```julia
DragScalar(
    label,
    data_type::Union{CImGui.lib.ImGuiDataType_, Integer},
    p_data
) -> Bool
DragScalar(
    label,
    data_type::Union{CImGui.lib.ImGuiDataType_, Integer},
    p_data,
    v_speed
) -> Bool
DragScalar(
    label,
    data_type::Union{CImGui.lib.ImGuiDataType_, Integer},
    p_data,
    v_speed,
    p_min
) -> Bool
DragScalar(
    label,
    data_type::Union{CImGui.lib.ImGuiDataType_, Integer},
    p_data,
    v_speed,
    p_min,
    p_max
) -> Bool
DragScalar(
    label,
    data_type::Union{CImGui.lib.ImGuiDataType_, Integer},
    p_data,
    v_speed,
    p_min,
    p_max,
    format
) -> Bool
DragScalar(
    label,
    data_type::Union{CImGui.lib.ImGuiDataType_, Integer},
    p_data,
    v_speed,
    p_min,
    p_max,
    format,
    flags::Union{CImGui.lib.ImGuiSliderFlags_, Integer}
) -> Bool

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L613).
