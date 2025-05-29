```julia
SetWindowPos(
    window::Ref{CImGui.lib.ImGuiWindow},
    pos::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
)
SetWindowPos(
    window::Ref{CImGui.lib.ImGuiWindow},
    pos::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    cond::Union{CImGui.lib.ImGuiCond_, Integer}
)

```

!!! warning
    This function is internal, it may change in the future.


[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui_internal.h#L3234).
