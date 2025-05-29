```julia
IsRectVisible(
    rect_min::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    rect_max::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
) -> Bool

```

矩形（画面空間内）が表示されているか、クリッピングされていないかをテストします。ユーザー側で粗いクリッピングを行うために使用します。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L979).
