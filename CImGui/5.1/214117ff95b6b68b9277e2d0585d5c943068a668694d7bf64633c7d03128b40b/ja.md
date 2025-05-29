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
    この関数は内部的なものであり、将来的に変更される可能性があります。


[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui_internal.h#L3234).
