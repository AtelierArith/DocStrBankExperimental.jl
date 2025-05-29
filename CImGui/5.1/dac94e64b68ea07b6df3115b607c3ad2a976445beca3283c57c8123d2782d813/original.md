```julia
IsMouseDoubleClicked(
    button::Union{CImGui.lib.ImGuiMouseButton_, Integer}
) -> Bool

```

Did mouse button double-clicked? Same as GetMouseClickedCount() == 2. (note that a double-click will also report IsMouseClicked() == true).

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L1041).
