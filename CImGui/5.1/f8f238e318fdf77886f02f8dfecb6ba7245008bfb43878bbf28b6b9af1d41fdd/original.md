```julia
BeginDragDropTarget() -> Bool

```

Call after submitting an item that may receive a payload. If this returns true, you can call AcceptDragDropPayload() + EndDragDropTarget().

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L918).
