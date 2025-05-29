```julia
GetForegroundDrawList() -> Ptr{CImGui.lib.ImDrawList}
GetForegroundDrawList(
    viewport::Union{Ptr{Nothing}, Ref{CImGui.lib.ImGuiViewport}}
) -> Ptr{CImGui.lib.ImDrawList}

```

指定されたビューポートまたは現在のウィンドウに関連付けられたビューポートの前景描画リストを取得します。この描画リストは、最上位にレンダリングされるものになります。dear imguiのコンテンツの上に形状やテキストを迅速に描画するのに便利です。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L975).
