```julia
SetAppAcceptingEvents(
    self::Ptr{CImGui.lib.ImGuiIO},
    accepting_events
)

```

キー/マウス/テキストイベントを受け入れるためのマスターフラグを設定します（デフォルトはtrue）。ネイティブダイアログボックスがアプリケーションループ/リフレッシュを中断している場合に便利で、アプリがフリーズしている間にイベントがキューに入るのを無効にしたい場合に使用します。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L2451).
