```julia
SetNextWindowSize(
    size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
)
SetNextWindowSize(
    size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    cond::Union{CImGui.lib.ImGuiCond_, Integer}
)

```

Set next window size. set axis to 0.0f to force an auto-fit on this axis. call before Begin().

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L419).
