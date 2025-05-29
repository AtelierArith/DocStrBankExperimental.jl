```julia
AddBezierQuadratic(
    self::Ptr{CImGui.lib.ImDrawList},
    p1::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    p2::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    p3::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    col::Integer,
    thickness
)
AddBezierQuadratic(
    self::Ptr{CImGui.lib.ImDrawList},
    p1::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    p2::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    p3::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    col::Integer,
    thickness,
    num_segments
)

```

二次ベジェ曲線（3つの制御点）。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3245).
