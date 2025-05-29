```julia
TabItemButton(label) -> Bool
TabItemButton(
    label,
    flags::Union{CImGui.lib.ImGuiTabItemFlags_, Integer}
) -> Bool

```

ボタンのように動作するタブを作成します。クリックされたときにtrueを返します。タブバーで選択することはできません。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L877).
