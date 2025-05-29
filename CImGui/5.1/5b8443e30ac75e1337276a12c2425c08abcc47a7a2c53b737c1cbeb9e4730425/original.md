```julia
IsMouseHoveringRect(
    r_min::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    r_max::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
) -> Bool
IsMouseHoveringRect(
    r_min::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    r_max::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    clip
) -> Bool

```

Is mouse hovering given bounding rect (in screen space). clipped by current clipping settings, but disregarding of other consideration of focus/window ordering/popup-block.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L1044).
