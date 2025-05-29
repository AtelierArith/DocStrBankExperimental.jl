```julia
IsMouseClicked(
    button::Union{CImGui.lib.ImGuiMouseButton_, Integer}
) -> Bool
IsMouseClicked(
    button::Union{CImGui.lib.ImGuiMouseButton_, Integer},
    repeat::Bool
) -> Bool

```

マウスボタンがクリックされましたか？（!DownからDownに移行しました）。GetMouseClickedCount() == 1と同じです。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L1039).
