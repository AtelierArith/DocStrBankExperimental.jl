```julia
IsMouseDoubleClicked(
    button::Union{CImGui.lib.ImGuiMouseButton_, Integer}
) -> Bool

```

マウスボタンがダブルクリックされましたか？ GetMouseClickedCount() == 2 と同じです。（ダブルクリックは IsMouseClicked() == true も報告します）。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L1041).
