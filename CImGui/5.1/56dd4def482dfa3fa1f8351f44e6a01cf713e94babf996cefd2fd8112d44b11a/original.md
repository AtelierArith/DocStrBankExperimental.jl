```julia
AddEllipse(
    self::Ptr{CImGui.lib.ImDrawList},
    center::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    radius::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    col::Integer
)
AddEllipse(
    self::Ptr{CImGui.lib.ImDrawList},
    center::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    radius::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    col::Integer,
    rot
)
AddEllipse(
    self::Ptr{CImGui.lib.ImDrawList},
    center::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    radius::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    col::Integer,
    rot,
    num_segments
)
AddEllipse(
    self::Ptr{CImGui.lib.ImDrawList},
    center::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    radius::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    col::Integer,
    rot,
    num_segments,
    thickness
)

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3240).
