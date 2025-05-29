```julia
GetMouseDragDelta() -> CImGui.lib.ImVec2
GetMouseDragDelta(
    button::Union{CImGui.lib.ImGuiMouseButton_, Integer}
) -> CImGui.lib.ImVec2
GetMouseDragDelta(
    button::Union{CImGui.lib.ImGuiMouseButton_, Integer},
    lock_threshold
) -> CImGui.lib.ImVec2

```

Return the delta from the initial clicking position while the mouse button is pressed or was just released. This is locked and return 0.0f until the mouse moves past a distance threshold at least once (uses io.MouseDraggingThreshold if lock_threshold < 0.0f).

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L1050).
