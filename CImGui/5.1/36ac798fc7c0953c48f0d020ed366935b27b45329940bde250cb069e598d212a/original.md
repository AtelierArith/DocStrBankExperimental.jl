```julia
IsRectVisible(
    rect_min::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    rect_max::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
) -> Bool

```

Test if rectangle (in screen space) is visible / not clipped. to perform coarse clipping on user's side.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L979).
