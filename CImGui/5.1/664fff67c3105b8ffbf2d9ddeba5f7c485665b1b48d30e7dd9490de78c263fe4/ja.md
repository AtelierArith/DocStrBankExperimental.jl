```julia
DragInt3(label, v) -> Bool
DragInt3(label, v, v_speed) -> Bool
DragInt3(label, v, v_speed, v_min) -> Bool
DragInt3(label, v, v_speed, v_min, v_max) -> Bool
DragInt3(label, v, v_speed, v_min, v_max, format) -> Bool
DragInt3(
    label,
    v,
    v_speed,
    v_min,
    v_max,
    format,
    flags::Union{CImGui.lib.ImGuiSliderFlags_, Integer}
) -> Bool

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L610).
