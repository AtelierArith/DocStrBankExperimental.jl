```julia
GetMouseCursorTexData(
    self::Ptr{CImGui.lib.ImFontAtlas},
    cursor::Union{CImGui.lib.ImGuiMouseCursor_, Integer},
    out_offset::Union{Ptr{Nothing}, Ref{CImGui.lib.ImVec2}, Ref{Tuple{T, T} where T}},
    out_size::Union{Ptr{Nothing}, Ref{CImGui.lib.ImVec2}, Ref{Tuple{T, T} where T}},
    out_uv_border,
    out_uv_fill
) -> Bool

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3523).
