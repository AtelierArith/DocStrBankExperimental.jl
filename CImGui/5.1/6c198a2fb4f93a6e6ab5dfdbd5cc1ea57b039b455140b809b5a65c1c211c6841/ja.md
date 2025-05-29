```julia
AddRectFilled(
    self::Ptr{CImGui.lib.ImDrawList},
    p_min::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    p_max::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    col::Integer
)
AddRectFilled(
    self::Ptr{CImGui.lib.ImDrawList},
    p_min::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    p_max::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    col::Integer,
    rounding
)
AddRectFilled(
    self::Ptr{CImGui.lib.ImDrawList},
    p_min::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    p_max::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    col::Integer,
    rounding,
    flags::Union{CImGui.lib.ImDrawFlags_, Integer}
)

```

A: 左上, b: 右下 (== 左上 + サイズ).

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3230).
