```julia
GetBackgroundDrawList() -> Ptr{CImGui.lib.ImDrawList}
GetBackgroundDrawList(
    viewport::Union{Ptr{Nothing}, Ref{CImGui.lib.ImGuiViewport}}
) -> Ptr{CImGui.lib.ImDrawList}

```

Get background draw list for the given viewport or viewport associated to the current window. this draw list will be the first rendering one. Useful to quickly draw shapes/text behind dear imgui contents.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L974).
