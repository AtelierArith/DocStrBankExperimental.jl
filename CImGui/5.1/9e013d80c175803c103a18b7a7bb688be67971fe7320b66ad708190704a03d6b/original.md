```julia
AddFontFromFileTTF(
    self::Ptr{CImGui.lib.ImFontAtlas},
    filename,
    size_pixels
) -> Ptr{CImGui.lib.ImFont}
AddFontFromFileTTF(
    self::Ptr{CImGui.lib.ImFontAtlas},
    filename,
    size_pixels,
    font_cfg::Union{Ptr{Nothing}, Ref{CImGui.lib.ImFontConfig}}
) -> Ptr{CImGui.lib.ImFont}
AddFontFromFileTTF(
    self::Ptr{CImGui.lib.ImFontAtlas},
    filename,
    size_pixels,
    font_cfg::Union{Ptr{Nothing}, Ref{CImGui.lib.ImFontConfig}},
    glyph_ranges::Union{Ptr{Nothing}, Ref{UInt16}}
) -> Ptr{CImGui.lib.ImFont}

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3468).
