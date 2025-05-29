```julia
IsBuilt(self::Ptr{CImGui.lib.ImFontAtlas}) -> Bool

```

Bit ambiguous: used to detect when user didn't build texture but effectively we should check TexID != 0 except that would be backend dependent...

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3485).
