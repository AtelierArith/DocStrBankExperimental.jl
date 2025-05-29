```julia
IsItemClicked() -> Bool
IsItemClicked(
    mouse_button::Union{CImGui.lib.ImGuiMouseButton_, Integer}
) -> Bool

```

Is the last item hovered and mouse clicked on? (**)  == IsMouseClicked(mouse_button) && IsItemHovered()Important. (**) this is NOT equivalent to the behavior of e.g. Button(). Read comments in function definition.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L952).
