```julia
GetForegroundDrawList() -> Ptr{CImGui.lib.ImDrawList}
GetForegroundDrawList(
    viewport::Union{Ptr{Nothing}, Ref{CImGui.lib.ImGuiViewport}}
) -> Ptr{CImGui.lib.ImDrawList}

```

Get foreground draw list for the given viewport or viewport associated to the current window. this draw list will be the top-most rendered one. Useful to quickly draw shapes/text over dear imgui contents.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L975).
