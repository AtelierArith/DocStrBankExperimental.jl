```julia
SetNextWindowClass(
    window_class::Union{Ptr{Nothing}, Ref{CImGui.lib.ImGuiWindowClass}}
)

```

次のウィンドウクラスを設定します（ドッキング互換性の制御 + カスタムビューポートフラグとプラットフォームの親/子関係を介してプラットフォームバックエンドへのヒントを提供）。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L896).
