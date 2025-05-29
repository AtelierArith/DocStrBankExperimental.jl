```julia
AddRemapChar(
    self::Ptr{CImGui.lib.ImFont},
    dst::UInt16,
    src::UInt16
)
AddRemapChar(
    self::Ptr{CImGui.lib.ImFont},
    dst::UInt16,
    src::UInt16,
    overwrite_dst
)

```

Makes 'dst' character/glyph points to 'src' character/glyph. Currently needs to be called AFTER fonts have been built.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3615).
