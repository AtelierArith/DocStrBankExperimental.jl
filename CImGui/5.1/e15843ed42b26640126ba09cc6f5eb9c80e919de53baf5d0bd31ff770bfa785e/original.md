```julia
AcceptDragDropPayload(type) -> Ptr{CImGui.lib.ImGuiPayload}
AcceptDragDropPayload(
    type,
    flags::Union{CImGui.lib.ImGuiDragDropFlags_, Integer}
) -> Ptr{CImGui.lib.ImGuiPayload}

```

Accept contents of a given type. If ImGuiDragDropFlags_AcceptBeforeDelivery is set you can peek into the payload before the mouse button is released.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L919).
