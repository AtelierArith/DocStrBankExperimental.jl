```julia
IsMouseDragging(
    button::Union{CImGui.lib.ImGuiMouseButton_, Integer}
) -> Bool
IsMouseDragging(
    button::Union{CImGui.lib.ImGuiMouseButton_, Integer},
    lock_threshold
) -> Bool

```

Is mouse dragging? (uses io.MouseDraggingThreshold if lock_threshold < 0.0f).

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L1049).
