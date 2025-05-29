```julia
AddFontFromMemoryTTF(
    self::Ptr{CImGui.lib.ImFontAtlas},
    font_data,
    font_data_size,
    size_pixels
) -> Ptr{CImGui.lib.ImFont}
AddFontFromMemoryTTF(
    self::Ptr{CImGui.lib.ImFontAtlas},
    font_data,
    font_data_size,
    size_pixels,
    font_cfg::Union{Ptr{Nothing}, Ref{CImGui.lib.ImFontConfig}}
) -> Ptr{CImGui.lib.ImFont}
AddFontFromMemoryTTF(
    self::Ptr{CImGui.lib.ImFontAtlas},
    font_data,
    font_data_size,
    size_pixels,
    font_cfg::Union{Ptr{Nothing}, Ref{CImGui.lib.ImFontConfig}},
    glyph_ranges::Union{Ptr{Nothing}, Ref{UInt16}}
) -> Ptr{CImGui.lib.ImFont}

```

Note: Transfer ownership of 'ttf*data' to ImFontAtlas! Will be deleted after destruction of the atlas. Set font*cfg->FontDataOwnedByAtlas=false to keep ownership of your data and it won't be freed.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3469).
