```julia
SliderScalarN(
    label,
    data_type::Union{CImGui.lib.ImGuiDataType_, Integer},
    p_data,
    components,
    p_min,
    p_max
) -> Bool
SliderScalarN(
    label,
    data_type::Union{CImGui.lib.ImGuiDataType_, Integer},
    p_data,
    components,
    p_min,
    p_max,
    format
) -> Bool
SliderScalarN(
    label,
    data_type::Union{CImGui.lib.ImGuiDataType_, Integer},
    p_data,
    components,
    p_min,
    p_max,
    format,
    flags::Union{CImGui.lib.ImGuiSliderFlags_, Integer}
) -> Bool

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L632).
