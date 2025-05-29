```julia
SetWindowPos(
    name::Union{Ptr{Int8}, String},
    pos::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
)
SetWindowPos(
    name::Union{Ptr{Int8}, String},
    pos::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    cond::Union{CImGui.lib.ImGuiCond_, Integer}
)

```

Set named window position.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L432).
