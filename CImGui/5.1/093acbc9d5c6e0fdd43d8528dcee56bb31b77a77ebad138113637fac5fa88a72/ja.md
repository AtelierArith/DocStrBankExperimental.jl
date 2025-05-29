```julia
AddFontFromMemoryCompressedTTF(
    self::Ptr{CImGui.lib.ImFontAtlas},
    compressed_font_data,
    compressed_font_data_size,
    size_pixels
) -> Ptr{CImGui.lib.ImFont}
AddFontFromMemoryCompressedTTF(
    self::Ptr{CImGui.lib.ImFontAtlas},
    compressed_font_data,
    compressed_font_data_size,
    size_pixels,
    font_cfg::Union{Ptr{Nothing}, Ref{CImGui.lib.ImFontConfig}}
) -> Ptr{CImGui.lib.ImFont}
AddFontFromMemoryCompressedTTF(
    self::Ptr{CImGui.lib.ImFontAtlas},
    compressed_font_data,
    compressed_font_data_size,
    size_pixels,
    font_cfg::Union{Ptr{Nothing}, Ref{CImGui.lib.ImFontConfig}},
    glyph_ranges::Union{Ptr{Nothing}, Ref{UInt16}}
) -> Ptr{CImGui.lib.ImFont}

```

'compressed*font*data' は呼び出し元によって所有されています。 binary*to*compressed_c.cpp で圧縮してください。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3470).
