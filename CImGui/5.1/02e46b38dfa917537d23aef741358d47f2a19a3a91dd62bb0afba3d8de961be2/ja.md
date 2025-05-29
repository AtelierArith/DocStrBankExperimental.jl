```julia
GetDragDropPayload() -> Ptr{CImGui.lib.ImGuiPayload}

```

どこからでも現在のペイロードを直接覗きます。ドラッグアンドドロップが終了または非アクティブな場合はNULLを返します。ペイロードタイプをテストするにはImGuiPayload::IsDataType()を使用します。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L921).
