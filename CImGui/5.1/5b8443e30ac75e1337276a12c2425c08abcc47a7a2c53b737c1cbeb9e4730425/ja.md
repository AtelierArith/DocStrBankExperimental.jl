```julia
IsMouseHoveringRect(
    r_min::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    r_max::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
) -> Bool
IsMouseHoveringRect(
    r_min::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    r_max::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    clip
) -> Bool

```

マウスが与えられたバウンディング矩形（スクリーンスペース内）にホバーしているかどうかを判断します。現在のクリッピング設定によってクリップされますが、フォーカス/ウィンドウの順序/ポップアップブロックの他の考慮事項は無視されます。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L1044).
