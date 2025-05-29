```julia
InvisibleButton(
    str_id,
    size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
) -> Bool
InvisibleButton(
    str_id,
    size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    flags::Union{CImGui.lib.ImGuiButtonFlags_, Integer}
) -> Bool

```

Flexible button behavior without the visuals, frequently useful to build custom behaviors using the public api (along with IsItemActive, IsItemHovered, etc.).

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L562).
