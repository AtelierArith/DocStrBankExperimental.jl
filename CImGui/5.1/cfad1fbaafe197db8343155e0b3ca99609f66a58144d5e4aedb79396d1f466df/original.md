```julia
DragFloat4(label, v) -> Bool
DragFloat4(label, v, v_speed) -> Bool
DragFloat4(label, v, v_speed, v_min) -> Bool
DragFloat4(label, v, v_speed, v_min, v_max) -> Bool
DragFloat4(label, v, v_speed, v_min, v_max, format) -> Bool
DragFloat4(
    label,
    v,
    v_speed,
    v_min,
    v_max,
    format,
    flags::Union{CImGui.lib.ImGuiSliderFlags_, Integer}
) -> Bool

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L606).
