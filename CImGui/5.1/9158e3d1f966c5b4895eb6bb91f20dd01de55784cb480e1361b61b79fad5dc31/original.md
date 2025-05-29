```julia
Selectable(
    label::Union{Ptr{Int8}, Ptr{Nothing}, String},
    p_selected::Ref{Bool}
) -> Bool
Selectable(
    label::Union{Ptr{Int8}, Ptr{Nothing}, String},
    p_selected::Ref{Bool},
    flags::Union{CImGui.lib.ImGuiSelectableFlags_, Integer}
) -> Bool
Selectable(
    label::Union{Ptr{Int8}, Ptr{Nothing}, String},
    p_selected::Ref{Bool},
    flags::Union{CImGui.lib.ImGuiSelectableFlags_, Integer},
    size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
) -> Bool

```

"bool* p_selected" point to the selection state (read-write), as a convenient helper.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L690).
