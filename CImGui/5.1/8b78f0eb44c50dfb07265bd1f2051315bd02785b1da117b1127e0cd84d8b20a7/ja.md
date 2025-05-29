```julia
AddRanges(
    self::Ptr{CImGui.lib.ImFontGlyphRangesBuilder},
    ranges::Union{Ptr{Nothing}, Ref{UInt16}}
)

```

範囲を追加します。例えば、builder.AddRanges(ImFontAtlas::GetGlyphRangesDefault())を使用して、すべてのASCII/ラテン+拡張を強制的に追加します。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3416).
