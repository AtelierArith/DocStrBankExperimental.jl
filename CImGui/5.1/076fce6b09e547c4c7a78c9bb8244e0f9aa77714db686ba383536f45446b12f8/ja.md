```julia
PathRect(
    self::Ptr{CImGui.lib.ImDrawList},
    rect_min::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    rect_max::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
)
PathRect(
    self::Ptr{CImGui.lib.ImDrawList},
    rect_min::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    rect_max::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    rounding
)
PathRect(
    self::Ptr{CImGui.lib.ImDrawList},
    rect_min::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    rect_max::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    rounding,
    flags::Union{CImGui.lib.ImDrawFlags_, Integer}
)

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3276).
