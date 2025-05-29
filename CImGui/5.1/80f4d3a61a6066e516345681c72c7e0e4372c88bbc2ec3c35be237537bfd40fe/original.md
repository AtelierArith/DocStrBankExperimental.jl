```julia
OpenPopupOnItemClick()
OpenPopupOnItemClick(str_id)
OpenPopupOnItemClick(
    str_id,
    popup_flags::Union{CImGui.lib.ImGuiPopupFlags_, Integer}
)

```

Helper to open popup when clicked on last item. Default to ImGuiPopupFlags*MouseButtonRight == 1. (note: actually triggers on the mouse _released* event to be consistent with popup behaviors).

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L785).
