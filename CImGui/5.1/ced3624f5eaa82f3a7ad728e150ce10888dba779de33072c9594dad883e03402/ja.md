```julia
BeginDragDropSource() -> Bool
BeginDragDropSource(
    flags::Union{CImGui.lib.ImGuiDragDropFlags_, Integer}
) -> Bool

```

アイテムをドラッグ可能として提出した後に呼び出します。これがtrueを返すと、SetDragDropPayload() + EndDragDropSource()を呼び出すことができます。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L915).
