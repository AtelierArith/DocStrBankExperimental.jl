```julia
SliderFloat(label, v, v_min, v_max) -> Bool
SliderFloat(label, v, v_min, v_max, format) -> Bool
SliderFloat(
    label,
    v,
    v_min,
    v_max,
    format,
    flags::Union{CImGui.lib.ImGuiSliderFlags_, Integer}
) -> Bool

```

Adjust format to decorate the value with a prefix or a suffix for in-slider labels or unit display.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L622).
