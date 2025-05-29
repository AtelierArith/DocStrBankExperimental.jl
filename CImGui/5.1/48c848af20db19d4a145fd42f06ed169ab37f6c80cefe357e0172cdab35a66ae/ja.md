```julia
AddFontFromMemoryCompressedBase85TTF(
    self::Ptr{CImGui.lib.ImFontAtlas},
    compressed_font_data_base85,
    size_pixels
) -> Ptr{CImGui.lib.ImFont}
AddFontFromMemoryCompressedBase85TTF(
    self::Ptr{CImGui.lib.ImFontAtlas},
    compressed_font_data_base85,
    size_pixels,
    font_cfg::Union{Ptr{Nothing}, Ref{CImGui.lib.ImFontConfig}}
) -> Ptr{CImGui.lib.ImFont}
AddFontFromMemoryCompressedBase85TTF(
    self::Ptr{CImGui.lib.ImFontAtlas},
    compressed_font_data_base85,
    size_pixels,
    font_cfg::Union{Ptr{Nothing}, Ref{CImGui.lib.ImFontConfig}},
    glyph_ranges::Union{Ptr{Nothing}, Ref{UInt16}}
) -> Ptr{CImGui.lib.ImFont}

```

'compressed*font*data*base85' は呼び出し元によって所有されています。-base85 パラメータを使用して binary*to*compressed*c.cpp で圧縮します。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3471).
