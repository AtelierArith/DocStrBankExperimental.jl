```julia
AddPolyline(
    self::Ptr{CImGui.lib.ImDrawList},
    points::Union{Ptr{Nothing}, Ref{CImGui.lib.ImVec2}, Ref{Tuple{T, T} where T}},
    num_points,
    col::Integer,
    flags::Union{CImGui.lib.ImDrawFlags_, Integer},
    thickness
)

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3250).
