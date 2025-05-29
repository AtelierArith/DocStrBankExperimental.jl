```julia
GetBackgroundDrawList() -> Ptr{CImGui.lib.ImDrawList}
GetBackgroundDrawList(
    viewport::Union{Ptr{Nothing}, Ref{CImGui.lib.ImGuiViewport}}
) -> Ptr{CImGui.lib.ImDrawList}

```

指定されたビューポートまたは現在のウィンドウに関連付けられたビューポートの背景描画リストを取得します。この描画リストは最初のレンダリングリストになります。dear imgui のコンテンツの背後に形状やテキストを迅速に描画するのに便利です。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L974).
