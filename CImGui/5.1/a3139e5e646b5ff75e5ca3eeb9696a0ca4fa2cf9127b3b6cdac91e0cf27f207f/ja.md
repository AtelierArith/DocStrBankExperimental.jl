```julia
IsItemClicked() -> Bool
IsItemClicked(
    mouse_button::Union{CImGui.lib.ImGuiMouseButton_, Integer}
) -> Bool

```

最後のアイテムがホバーされ、マウスがクリックされましたか？ (**)  == IsMouseClicked(mouse_button) && IsItemHovered()重要です。 (**) これは、例えばButton()の動作と同等ではありません。関数定義のコメントを読んでください。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L952).
