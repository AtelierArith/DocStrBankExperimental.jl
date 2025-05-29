```julia
SetItemKeyOwner(key::CImGui.lib.ImGuiKey)

```

マウスオーバーまたはアクティブな場合、キーの所有者を最後のアイテムIDに設定します。 'if (IsItemHovered() || IsItemActive())  SetKeyOwner(key, GetItemID());' と同等です。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L1032).
