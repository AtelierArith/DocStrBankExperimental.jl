```julia
GetMouseClickedCount(
    button::Union{CImGui.lib.ImGuiMouseButton_, Integer}
) -> Int32

```

Return the number of successive mouse-clicks at the time where a click happen (otherwise 0).

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L1043).
