```julia
IsPopupOpen(
    str_id::Union{Ptr{Int8}, Ptr{Nothing}, String}
) -> Bool
IsPopupOpen(
    str_id::Union{Ptr{Int8}, Ptr{Nothing}, String},
    flags::Union{CImGui.lib.ImGuiPopupFlags_, Integer}
) -> Bool

```

Return true if the popup is open.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L801).
