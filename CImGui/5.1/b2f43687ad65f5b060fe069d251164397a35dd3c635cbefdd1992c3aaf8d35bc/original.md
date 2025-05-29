```julia
SetDragDropPayload(type, data, sz) -> Bool
SetDragDropPayload(
    type,
    data,
    sz,
    cond::Union{CImGui.lib.ImGuiCond_, Integer}
) -> Bool

```

Type is a user defined string of maximum 32 characters. Strings starting with '_' are reserved for dear imgui internal types. Data is copied and held by imgui. Return true when payload has been accepted.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L916).
