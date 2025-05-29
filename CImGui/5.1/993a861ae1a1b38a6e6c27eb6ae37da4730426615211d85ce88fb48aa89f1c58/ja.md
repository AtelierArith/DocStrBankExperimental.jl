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

注意: 'ttf*data' の所有権を ImFontAtlas に移転してください！ アトラスの破棄後に削除されます。 font*cfg->FontDataOwnedByAtlas=false を設定すると、データの所有権が保持され、解放されません。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3469).
