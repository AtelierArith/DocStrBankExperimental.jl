```julia
PathBezierQuadraticCurveTo(
    self::Ptr{CImGui.lib.ImDrawList},
    p2::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    p3::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
)
PathBezierQuadraticCurveTo(
    self::Ptr{CImGui.lib.ImDrawList},
    p2::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    p3::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    num_segments
)

```

Quadratic Bezier (3 control points).

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3275).
