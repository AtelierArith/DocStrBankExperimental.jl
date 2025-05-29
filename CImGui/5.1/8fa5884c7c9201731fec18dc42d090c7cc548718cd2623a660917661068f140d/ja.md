```julia
PathBezierCubicCurveTo(
    self::Ptr{CImGui.lib.ImDrawList},
    p2::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    p3::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    p4::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
)
PathBezierCubicCurveTo(
    self::Ptr{CImGui.lib.ImDrawList},
    p2::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    p3::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    p4::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    num_segments
)

```

三次ベジェ曲線（4つの制御点）。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3274).
