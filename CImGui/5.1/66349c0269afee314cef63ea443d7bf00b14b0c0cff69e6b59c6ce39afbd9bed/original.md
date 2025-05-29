```julia
DragIntRange2(label, v_current_min, v_current_max) -> Bool
DragIntRange2(
    label,
    v_current_min,
    v_current_max,
    v_speed
) -> Bool
DragIntRange2(
    label,
    v_current_min,
    v_current_max,
    v_speed,
    v_min
) -> Bool
DragIntRange2(
    label,
    v_current_min,
    v_current_max,
    v_speed,
    v_min,
    v_max
) -> Bool
DragIntRange2(
    label,
    v_current_min,
    v_current_max,
    v_speed,
    v_min,
    v_max,
    format
) -> Bool
DragIntRange2(
    label,
    v_current_min,
    v_current_max,
    v_speed,
    v_min,
    v_max,
    format,
    format_max
) -> Bool
DragIntRange2(
    label,
    v_current_min,
    v_current_max,
    v_speed,
    v_min,
    v_max,
    format,
    format_max,
    flags::Union{CImGui.lib.ImGuiSliderFlags_, Integer}
) -> Bool

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L612).
