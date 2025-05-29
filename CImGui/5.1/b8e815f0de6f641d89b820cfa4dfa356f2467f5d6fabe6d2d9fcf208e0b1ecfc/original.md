```julia
DragFloat2(label, v) -> Bool
DragFloat2(label, v, v_speed) -> Bool
DragFloat2(label, v, v_speed, v_min) -> Bool
DragFloat2(label, v, v_speed, v_min, v_max) -> Bool
DragFloat2(label, v, v_speed, v_min, v_max, format) -> Bool
DragFloat2(
    label,
    v,
    v_speed,
    v_min,
    v_max,
    format,
    flags::Union{CImGui.lib.ImGuiSliderFlags_, Integer}
) -> Bool

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L604).
