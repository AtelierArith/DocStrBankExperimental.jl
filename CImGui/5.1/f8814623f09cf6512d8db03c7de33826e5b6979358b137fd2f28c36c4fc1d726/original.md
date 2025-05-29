```julia
SetNextWindowClass(
    window_class::Union{Ptr{Nothing}, Ref{CImGui.lib.ImGuiWindowClass}}
)

```

Set next window class (control docking compatibility + provide hints to platform backend via custom viewport flags and platform parent/child relationship).

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L896).
