```julia
SetWindowCollapsed(collapsed::Bool)
SetWindowCollapsed(
    collapsed::Bool,
    cond::Union{CImGui.lib.ImGuiCond_, Integer}
)

```

(not recommended) set current window collapsed state. prefer using SetNextWindowCollapsed().

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L429).
