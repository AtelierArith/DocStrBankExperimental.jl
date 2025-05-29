```julia
PathEllipticalArcTo(
    self::Ptr{CImGui.lib.ImDrawList},
    center::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    radius::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    rot,
    a_min,
    a_max
)
PathEllipticalArcTo(
    self::Ptr{CImGui.lib.ImDrawList},
    center::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    radius::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    rot,
    a_min,
    a_max,
    num_segments
)

```

楕円。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3273).
