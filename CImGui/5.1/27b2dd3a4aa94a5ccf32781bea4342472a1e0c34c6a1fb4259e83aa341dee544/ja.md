```julia
DragInt4(label, v) -> Bool
DragInt4(label, v, v_speed) -> Bool
DragInt4(label, v, v_speed, v_min) -> Bool
DragInt4(label, v, v_speed, v_min, v_max) -> Bool
DragInt4(label, v, v_speed, v_min, v_max, format) -> Bool
DragInt4(
    label,
    v,
    v_speed,
    v_min,
    v_max,
    format,
    flags::Union{CImGui.lib.ImGuiSliderFlags_, Integer}
) -> Bool

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L611).
