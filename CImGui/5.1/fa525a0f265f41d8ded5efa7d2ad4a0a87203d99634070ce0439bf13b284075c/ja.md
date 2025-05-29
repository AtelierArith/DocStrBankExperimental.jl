```julia
IsWindowFocused() -> Bool
IsWindowFocused(
    flags::Union{CImGui.lib.ImGuiFocusedFlags_, Integer}
) -> Bool

```

現在のウィンドウはフォーカスされていますか？またはフラグに応じてそのルート/子です。オプションについてはフラグを参照してください。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L406).
