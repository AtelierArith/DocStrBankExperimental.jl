```julia
SetNextWindowPos(
    pos::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
)
SetNextWindowPos(
    pos::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    cond::Union{CImGui.lib.ImGuiCond_, Integer}
)
SetNextWindowPos(
    pos::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    cond::Union{CImGui.lib.ImGuiCond_, Integer},
    pivot::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
)

```

Set next window position. call before Begin(). use pivot=(0.5f,0.5f) to center on given point, etc.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L418).
