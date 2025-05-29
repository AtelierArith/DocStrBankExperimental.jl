```julia
SetItemKeyOwner(
    key::CImGui.lib.ImGuiKey,
    flags::Union{CImGui.lib.ImGuiInputFlags_, Integer}
)

```

最後のアイテムにマウスオーバーまたはアクティブな場合、キーの所有者を設定します。 'if (IsItemHovered() || IsItemActive())  SetKeyOwner(key, GetItemID());' と同等です。

!!! 警告     この関数は内部的なものであり、将来的に変更される可能性があります。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui_internal.h#L3467).
