```julia
IsMouseDragging(
    button::Union{CImGui.lib.ImGuiMouseButton_, Integer}
) -> Bool
IsMouseDragging(
    button::Union{CImGui.lib.ImGuiMouseButton_, Integer},
    lock_threshold
) -> Bool

```

マウスがドラッグされていますか？（lock_threshold < 0.0f の場合は io.MouseDraggingThreshold を使用します）。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L1049).
