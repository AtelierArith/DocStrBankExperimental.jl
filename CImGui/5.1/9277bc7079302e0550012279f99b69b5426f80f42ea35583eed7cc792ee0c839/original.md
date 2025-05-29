```julia
SetWindowPos(
    pos::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
)
SetWindowPos(
    pos::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    cond::Union{CImGui.lib.ImGuiCond_, Integer}
)

```

(not recommended) set current window position - call within Begin()/End(). prefer using SetNextWindowPos(), as this may incur tearing and side-effects.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L427).
