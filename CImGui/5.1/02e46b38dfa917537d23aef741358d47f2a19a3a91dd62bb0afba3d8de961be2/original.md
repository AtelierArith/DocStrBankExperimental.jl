```julia
GetDragDropPayload() -> Ptr{CImGui.lib.ImGuiPayload}

```

Peek directly into the current payload from anywhere. returns NULL when drag and drop is finished or inactive. use ImGuiPayload::IsDataType() to test for the payload type.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L921).
