```julia
IsRectVisible(
    size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
) -> Bool

```

矩形（指定されたサイズ、カーソル位置から開始）が表示されているかどうかをテストします / クリップされていないかどうか。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L978).
