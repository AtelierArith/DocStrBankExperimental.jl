```julia
ColorButton(
    desc_id,
    col::Union{CImGui.lib.ImVec4, NTuple{4, T} where T}
) -> Bool
ColorButton(
    desc_id,
    col::Union{CImGui.lib.ImVec4, NTuple{4, T} where T},
    flags::Union{CImGui.lib.ImGuiColorEditFlags_, Integer}
) -> Bool
ColorButton(
    desc_id,
    col::Union{CImGui.lib.ImVec4, NTuple{4, T} where T},
    flags::Union{CImGui.lib.ImGuiColorEditFlags_, Integer},
    size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
) -> Bool

```

色の四角形/ボタンを表示し、詳細を表示するためにホバーし、押されたときにtrueを返します。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L662).
