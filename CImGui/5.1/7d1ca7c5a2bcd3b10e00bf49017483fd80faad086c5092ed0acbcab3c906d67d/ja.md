```julia
AddNgon(
    self::Ptr{CImGui.lib.ImDrawList},
    center::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    radius,
    col::Integer,
    num_segments
)
AddNgon(
    self::Ptr{CImGui.lib.ImDrawList},
    center::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    radius,
    col::Integer,
    num_segments,
    thickness
)

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3238).
