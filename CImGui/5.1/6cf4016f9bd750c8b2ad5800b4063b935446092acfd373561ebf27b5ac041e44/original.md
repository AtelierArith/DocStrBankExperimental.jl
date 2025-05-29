```julia
BeginPopupContextVoid() -> Bool
BeginPopupContextVoid(str_id) -> Bool
BeginPopupContextVoid(
    str_id,
    popup_flags::Union{CImGui.lib.ImGuiPopupFlags_, Integer}
) -> Bool

```

Open+begin popup when clicked in void (where there are no windows).

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L795).
