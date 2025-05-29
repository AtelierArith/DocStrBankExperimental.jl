```julia
RenderText(
    self::Ptr{CImGui.lib.ImFont},
    draw_list::Union{Ptr{Nothing}, Ref{CImGui.lib.ImDrawList}},
    size,
    pos::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    col::Integer,
    clip_rect::Union{CImGui.lib.ImVec4, NTuple{4, T} where T},
    text_begin,
    text_end
)
RenderText(
    self::Ptr{CImGui.lib.ImFont},
    draw_list::Union{Ptr{Nothing}, Ref{CImGui.lib.ImDrawList}},
    size,
    pos::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    col::Integer,
    clip_rect::Union{CImGui.lib.ImVec4, NTuple{4, T} where T},
    text_begin,
    text_end,
    wrap_width
)
RenderText(
    self::Ptr{CImGui.lib.ImFont},
    draw_list::Union{Ptr{Nothing}, Ref{CImGui.lib.ImDrawList}},
    size,
    pos::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    col::Integer,
    clip_rect::Union{CImGui.lib.ImVec4, NTuple{4, T} where T},
    text_begin,
    text_end,
    wrap_width,
    cpu_fine_clip
)

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3608).
