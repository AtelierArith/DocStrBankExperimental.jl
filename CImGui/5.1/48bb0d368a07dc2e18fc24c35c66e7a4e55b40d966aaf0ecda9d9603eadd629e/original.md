```julia
BeginPopupContextWindow() -> Bool
BeginPopupContextWindow(str_id) -> Bool
BeginPopupContextWindow(
    str_id,
    popup_flags::Union{CImGui.lib.ImGuiPopupFlags_, Integer}
) -> Bool

```

Open+begin popup when clicked on current window.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L794).
