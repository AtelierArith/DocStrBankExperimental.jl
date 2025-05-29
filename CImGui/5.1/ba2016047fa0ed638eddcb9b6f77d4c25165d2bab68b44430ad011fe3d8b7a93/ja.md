```julia
IsWindowHovered() -> Bool
IsWindowHovered(
    flags::Union{CImGui.lib.ImGuiHoveredFlags_, Integer}
) -> Bool

```

現在のウィンドウがホバーされていて、ホバー可能であるか（例：ポップアップ/モーダルによってブロックされていないか）を確認します。オプションについてはImGuiHoveredFlags_を参照してください。重要：マウスがDear ImGuiに送信されるべきか、基盤アプリに送信されるべきかを確認しようとしている場合は、この関数を使用しないでください！そのためには、'io.WantCaptureMouse'ブール値を使用してください！詳細については、FAQの「Dear ImGuiまたはアプリケーションにマウス/キーボードを送信するかどうかを判断するにはどうすればよいですか？」の項目を参照してください。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L407).
