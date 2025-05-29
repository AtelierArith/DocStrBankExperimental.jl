```julia
SetItemKeyOwner(key::CImGui.lib.ImGuiKey)

```

Set key owner to last item ID if it is hovered or active. Equivalent to 'if (IsItemHovered() || IsItemActive())  SetKeyOwner(key, GetItemID());'.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L1032).
