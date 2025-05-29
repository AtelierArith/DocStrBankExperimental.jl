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

マウスボタンが押されている間、またはちょうど解放されたときの初期クリック位置からのデルタを返します。これはロックされており、マウスが距離のしきい値を少なくとも一度超えるまで0.0fを返します（lock_threshold < 0.0fの場合はio.MouseDraggingThresholdを使用します）。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L1050).
