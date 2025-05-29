```julia
SetWindowSize(
    name::Union{Ptr{Int8}, String},
    size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
)
SetWindowSize(
    name::Union{Ptr{Int8}, String},
    size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    cond::Union{CImGui.lib.ImGuiCond_, Integer}
)

```

Set named window size. set axis to 0.0f to force an auto-fit on this axis.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L433).
