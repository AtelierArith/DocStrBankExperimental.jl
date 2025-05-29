```julia
BeginDragDropSource() -> Bool
BeginDragDropSource(
    flags::Union{CImGui.lib.ImGuiDragDropFlags_, Integer}
) -> Bool

```

Call after submitting an item which may be dragged. when this return true, you can call SetDragDropPayload() + EndDragDropSource().

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L915).
