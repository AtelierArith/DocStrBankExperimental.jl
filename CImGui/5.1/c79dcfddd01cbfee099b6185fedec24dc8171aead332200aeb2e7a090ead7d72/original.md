```julia
CollapsingHeader(
    label::Union{Ptr{Int8}, Ptr{Nothing}, String},
    p_visible::Union{Ptr{Nothing}, Ref{Bool}}
) -> Bool
CollapsingHeader(
    label::Union{Ptr{Int8}, Ptr{Nothing}, String},
    p_visible::Union{Ptr{Nothing}, Ref{Bool}},
    flags::Union{CImGui.lib.ImGuiTreeNodeFlags_, Integer}
) -> Bool

```

When 'p*visible != NULL': if '*p*visible==true' display an additional small close button on upper right of the header which will set the bool to false when clicked, if '*p_visible==false' don't display the header.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L682).
