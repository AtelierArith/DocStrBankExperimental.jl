```julia
GetStyle() -> Ptr{CImGui.lib.ImGuiStyle}

```

スタイル構造体（色、サイズ）にアクセスします。フレームの途中でスタイルを変更するには、常にPushStyleColor()、PushStyleVar()を使用してください！

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L342).
