```julia
SetNextWindowContentSize(
    size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
)

```

次のウィンドウのコンテンツサイズを設定します（~ スクロール可能なクライアントエリア、スクロールバーの範囲を強制します）。ウィンドウの装飾（タイトルバー、メニューバーなど）やWindowPaddingは含まれません。自動にするには、軸を0.0fに設定します。Begin()の前に呼び出してください。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L421).
