```julia
AddRanges(
    self::Ptr{CImGui.lib.ImFontGlyphRangesBuilder},
    ranges::Union{Ptr{Nothing}, Ref{UInt16}}
)

```

Add ranges, e.g. builder.AddRanges(ImFontAtlas::GetGlyphRangesDefault()) to force add all of ASCII/Latin+Ext.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3416).
