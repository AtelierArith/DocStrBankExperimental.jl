```julia
AcceptDragDropPayload(type) -> Ptr{CImGui.lib.ImGuiPayload}
AcceptDragDropPayload(
    type,
    flags::Union{CImGui.lib.ImGuiDragDropFlags_, Integer}
) -> Ptr{CImGui.lib.ImGuiPayload}

```

指定されたタイプの内容を受け入れます。ImGuiDragDropFlags_AcceptBeforeDeliveryが設定されている場合、マウスボタンが放される前にペイロードを覗くことができます。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L919).
