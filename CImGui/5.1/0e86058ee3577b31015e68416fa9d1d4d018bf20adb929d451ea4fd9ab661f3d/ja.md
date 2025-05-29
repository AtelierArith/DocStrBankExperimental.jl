```julia
DragFloat(label, v) -> Bool
DragFloat(label, v, v_speed) -> Bool
DragFloat(label, v, v_speed, v_min) -> Bool
DragFloat(label, v, v_speed, v_min, v_max) -> Bool
DragFloat(label, v, v_speed, v_min, v_max, format) -> Bool
DragFloat(
    label,
    v,
    v_speed,
    v_min,
    v_max,
    format,
    flags::Union{CImGui.lib.ImGuiSliderFlags_, Integer}
) -> Bool

```

もし v*min >= v*max であれば、境界はありません。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L603).
