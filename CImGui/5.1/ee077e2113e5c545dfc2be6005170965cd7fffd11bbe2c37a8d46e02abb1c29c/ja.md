```julia
SetColorEditOptions(
    flags::Union{CImGui.lib.ImGuiColorEditFlags_, Integer}
)

```

現在のオプションを初期化します（一般的にはアプリケーションの起動時）デフォルトのフォーマット、ピッカータイプなどを選択したい場合。ユーザーは多くの設定を変更できますが、呼び出しに_NoOptionsフラグを渡すと変更できなくなります。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L663).
