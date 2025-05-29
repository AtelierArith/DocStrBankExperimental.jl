```julia
SliderAngle(label, v_rad) -> Bool
SliderAngle(label, v_rad, v_degrees_min) -> Bool
SliderAngle(
    label,
    v_rad,
    v_degrees_min,
    v_degrees_max
) -> Bool
SliderAngle(
    label,
    v_rad,
    v_degrees_min,
    v_degrees_max,
    format
) -> Bool
SliderAngle(
    label,
    v_rad,
    v_degrees_min,
    v_degrees_max,
    format,
    flags::Union{CImGui.lib.ImGuiSliderFlags_, Integer}
) -> Bool

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L626).
