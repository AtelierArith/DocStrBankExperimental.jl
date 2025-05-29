```julia
RenderChar(
    self::Ptr{CImGui.lib.ImFont},
    draw_list::Union{Ptr{Nothing}, Ref{CImGui.lib.ImDrawList}},
    size,
    pos::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    col::Integer,
    c::UInt16
)

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3607).
