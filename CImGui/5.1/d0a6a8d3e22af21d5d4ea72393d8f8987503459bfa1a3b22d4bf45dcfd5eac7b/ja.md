```julia
GetWindowPos() -> CImGui.lib.ImVec2

```

現在のウィンドウの位置をスクリーンスペースで取得します（これを使用する必要があるのは非常に稀です。常に GetCursorScreenPos() と GetContentRegionAvail() を使用することを検討してください）。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L410).
