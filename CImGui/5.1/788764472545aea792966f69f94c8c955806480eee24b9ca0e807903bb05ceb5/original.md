```julia
BeginPopupContextItem() -> Bool
BeginPopupContextItem(str_id) -> Bool
BeginPopupContextItem(
    str_id,
    popup_flags::Union{CImGui.lib.ImGuiPopupFlags_, Integer}
) -> Bool

```

Open+begin popup when clicked on last item. Use str_id==NULL to associate the popup to previous item. If you want to use that on a non-interactive item such as Text() you need to pass in an explicit ID here. read comments in .cpp!

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L793).
