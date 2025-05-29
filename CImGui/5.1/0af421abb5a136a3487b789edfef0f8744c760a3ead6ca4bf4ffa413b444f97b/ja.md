```julia
Selectable(
    label::Union{Ptr{Int8}, Ptr{Nothing}, String}
) -> Bool
Selectable(
    label::Union{Ptr{Int8}, Ptr{Nothing}, String},
    selected::Bool
) -> Bool
Selectable(
    label::Union{Ptr{Int8}, Ptr{Nothing}, String},
    selected::Bool,
    flags::Union{CImGui.lib.ImGuiSelectableFlags_, Integer}
) -> Bool
Selectable(
    label::Union{Ptr{Int8}, Ptr{Nothing}, String},
    selected::Bool,
    flags::Union{CImGui.lib.ImGuiSelectableFlags_, Integer},
    size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
) -> Bool

```

"bool selected" は選択状態を保持します（読み取り専用）。Selectable() がクリックされると true を返すので、選択状態を変更できます。size.x==0.0: 残りの幅を使用、size.x>0.0: 幅を指定。size.y==0.0: ラベルの高さを使用、size.y>0.0: 高さを指定。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L689).
