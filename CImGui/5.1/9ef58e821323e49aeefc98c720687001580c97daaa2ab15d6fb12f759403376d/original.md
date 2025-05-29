```julia
AddCustomRectFontGlyph(
    self::Ptr{CImGui.lib.ImFontAtlas},
    font::Union{Ptr{Nothing}, Ref{CImGui.lib.ImFont}},
    id::UInt16,
    width,
    height,
    advance_x
) -> Int32
AddCustomRectFontGlyph(
    self::Ptr{CImGui.lib.ImFontAtlas},
    font::Union{Ptr{Nothing}, Ref{CImGui.lib.ImFont}},
    id::UInt16,
    width,
    height,
    advance_x,
    offset::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
) -> Int32

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3518).
