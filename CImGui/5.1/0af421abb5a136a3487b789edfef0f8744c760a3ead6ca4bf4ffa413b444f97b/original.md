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

"bool selected" carry the selection state (read-only). Selectable() is clicked is returns true so you can modify your selection state. size.x==0.0: use remaining width, size.x>0.0: specify width. size.y==0.0: use label height, size.y>0.0: specify height.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L689).
