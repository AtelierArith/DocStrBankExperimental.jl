```julia
SetWindowSize(
    size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
)
SetWindowSize(
    size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    cond::Union{CImGui.lib.ImGuiCond_, Integer}
)

```

(not recommended) set current window size - call within Begin()/End(). set to ImVec2(0, 0) to force an auto-fit. prefer using SetNextWindowSize(), as this may incur tearing and minor side-effects.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L428).
