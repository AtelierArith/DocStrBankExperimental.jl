```julia
SetItemKeyOwner(
    key::CImGui.lib.ImGuiKey,
    flags::Union{CImGui.lib.ImGuiInputFlags_, Integer}
)

```

Set key owner to last item if it is hovered or active. Equivalent to 'if (IsItemHovered() || IsItemActive())  SetKeyOwner(key, GetItemID());'.

!!! warning
    This function is internal, it may change in the future.


[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui_internal.h#L3467).
