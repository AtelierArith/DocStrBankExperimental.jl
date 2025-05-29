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

'dst' 文字/グリフを 'src' 文字/グリフにポイントさせます。現在、フォントが構築された後に呼び出す必要があります。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3615).
