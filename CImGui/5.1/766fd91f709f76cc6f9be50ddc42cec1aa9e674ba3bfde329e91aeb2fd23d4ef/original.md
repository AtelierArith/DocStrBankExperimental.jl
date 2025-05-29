```julia
DragInt(label, v) -> Bool
DragInt(label, v, v_speed) -> Bool
DragInt(label, v, v_speed, v_min) -> Bool
DragInt(label, v, v_speed, v_min, v_max) -> Bool
DragInt(label, v, v_speed, v_min, v_max, format) -> Bool
DragInt(
    label,
    v,
    v_speed,
    v_min,
    v_max,
    format,
    flags::Union{CImGui.lib.ImGuiSliderFlags_, Integer}
) -> Bool

```

If v*min >= v*max we have no bound.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L608).
