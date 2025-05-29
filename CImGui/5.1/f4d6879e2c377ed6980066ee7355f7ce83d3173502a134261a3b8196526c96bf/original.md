```julia
VSliderInt(
    label,
    size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    v,
    v_min,
    v_max
) -> Bool
VSliderInt(
    label,
    size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    v,
    v_min,
    v_max,
    format
) -> Bool
VSliderInt(
    label,
    size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    v,
    v_min,
    v_max,
    format,
    flags::Union{CImGui.lib.ImGuiSliderFlags_, Integer}
) -> Bool

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L634).
