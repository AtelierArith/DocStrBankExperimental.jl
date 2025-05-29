```julia
IsItemHovered() -> Bool
IsItemHovered(
    flags::Union{CImGui.lib.ImGuiHoveredFlags_, Integer}
) -> Bool

```

Is the last item hovered? (and usable, aka not blocked by a popup, etc.). See ImGuiHoveredFlags for more options.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L949).
