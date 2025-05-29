```julia
GetMouseCursor() -> Int32

```

希望するマウスカーソルの形状を取得します。重要: ImGui::NewFrame() でリセットします。これはフレーム中に更新されます。Render() の前に有効です。io.MouseDrawCursor を設定してソフトウェアレンダリングを使用する場合、ImGui がそれらをレンダリングします。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L1052).
