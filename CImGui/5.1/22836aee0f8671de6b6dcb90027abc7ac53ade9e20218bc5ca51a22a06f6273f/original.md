```julia
IsRectVisible(
    size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
) -> Bool

```

Test if rectangle (of given size, starting from cursor position) is visible / not clipped.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L978).
