```julia
IsItemHovered() -> Bool
IsItemHovered(
    flags::Union{CImGui.lib.ImGuiHoveredFlags_, Integer}
) -> Bool

```

最後のアイテムがホバーされていますか？（使用可能で、ポップアップなどにブロックされていない場合）。詳細なオプションについてはImGuiHoveredFlagsを参照してください。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L949).
