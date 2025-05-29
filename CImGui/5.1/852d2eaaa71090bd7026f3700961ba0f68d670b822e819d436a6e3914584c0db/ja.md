```julia
AddText(
    self::Ptr{CImGui.lib.ImDrawList},
    pos::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    col::Integer,
    text_begin::Union{Ptr{Int8}, Ptr{Nothing}, String}
)
AddText(
    self::Ptr{CImGui.lib.ImDrawList},
    pos::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    col::Integer,
    text_begin::Union{Ptr{Int8}, Ptr{Nothing}, String},
    text_end::Union{Ptr{Int8}, Ptr{Nothing}, String}
)

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3242).
