```julia
AddImageRounded(
    self::Ptr{CImGui.lib.ImDrawList},
    user_texture_id::UInt64,
    p_min::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    p_max::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    uv_min::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    uv_max::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    col::Integer,
    rounding
)
AddImageRounded(
    self::Ptr{CImGui.lib.ImDrawList},
    user_texture_id::UInt64,
    p_min::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    p_max::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    uv_min::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    uv_max::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    col::Integer,
    rounding,
    flags::Union{CImGui.lib.ImDrawFlags_, Integer}
)

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3260).
