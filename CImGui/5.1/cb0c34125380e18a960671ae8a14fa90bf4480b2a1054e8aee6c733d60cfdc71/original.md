```julia
AddText(
    self::Ptr{CImGui.lib.ImDrawList},
    font::Union{Ptr{Nothing}, Ref{CImGui.lib.ImFont}},
    font_size::Real,
    pos::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    col::Integer,
    text_begin::Union{Ptr{Int8}, Ptr{Nothing}, String}
)
AddText(
    self::Ptr{CImGui.lib.ImDrawList},
    font::Union{Ptr{Nothing}, Ref{CImGui.lib.ImFont}},
    font_size::Real,
    pos::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    col::Integer,
    text_begin::Union{Ptr{Int8}, Ptr{Nothing}, String},
    text_end::Union{Ptr{Int8}, Ptr{Nothing}, String}
)
AddText(
    self::Ptr{CImGui.lib.ImDrawList},
    font::Union{Ptr{Nothing}, Ref{CImGui.lib.ImFont}},
    font_size::Real,
    pos::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    col::Integer,
    text_begin::Union{Ptr{Int8}, Ptr{Nothing}, String},
    text_end::Union{Ptr{Int8}, Ptr{Nothing}, String},
    wrap_width::Real
)
AddText(
    self::Ptr{CImGui.lib.ImDrawList},
    font::Union{Ptr{Nothing}, Ref{CImGui.lib.ImFont}},
    font_size::Real,
    pos::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    col::Integer,
    text_begin::Union{Ptr{Int8}, Ptr{Nothing}, String},
    text_end::Union{Ptr{Int8}, Ptr{Nothing}, String},
    wrap_width::Real,
    cpu_fine_clip_rect::Union{Ptr{Nothing}, Ref{CImGui.lib.ImVec4}, Ref{NTuple{4, T} where T}}
)

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3243).
