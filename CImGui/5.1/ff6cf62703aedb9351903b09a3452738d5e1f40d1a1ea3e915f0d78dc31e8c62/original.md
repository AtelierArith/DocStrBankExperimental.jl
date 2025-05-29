```julia
IsMouseClicked(
    button::Union{CImGui.lib.ImGuiMouseButton_, Integer}
) -> Bool
IsMouseClicked(
    button::Union{CImGui.lib.ImGuiMouseButton_, Integer},
    repeat::Bool
) -> Bool

```

Did mouse button clicked? (went from !Down to Down). Same as GetMouseClickedCount() == 1.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L1039).
