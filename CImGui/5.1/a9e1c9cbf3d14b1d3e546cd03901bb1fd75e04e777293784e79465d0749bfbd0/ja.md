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

視覚的な要素なしでの柔軟なボタン動作は、カスタム動作を構築するために頻繁に便利です（IsItemActive、IsItemHoveredなどの公開APIとともに）。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L562).
