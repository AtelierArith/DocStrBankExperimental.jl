```julia
VSliderScalar(
    label,
    size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    data_type::Union{CImGui.lib.ImGuiDataType_, Integer},
    p_data,
    p_min,
    p_max
) -> Bool
VSliderScalar(
    label,
    size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    data_type::Union{CImGui.lib.ImGuiDataType_, Integer},
    p_data,
    p_min,
    p_max,
    format
) -> Bool
VSliderScalar(
    label,
    size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    data_type::Union{CImGui.lib.ImGuiDataType_, Integer},
    p_data,
    p_min,
    p_max,
    format,
    flags::Union{CImGui.lib.ImGuiSliderFlags_, Integer}
) -> Bool

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L635).
