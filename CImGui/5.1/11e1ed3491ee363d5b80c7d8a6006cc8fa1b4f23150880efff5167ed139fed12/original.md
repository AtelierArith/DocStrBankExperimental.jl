```julia
OpenPopup(str_id::Union{Ptr{Int8}, Ptr{Nothing}, String})
OpenPopup(
    str_id::Union{Ptr{Int8}, Ptr{Nothing}, String},
    popup_flags::Union{CImGui.lib.ImGuiPopupFlags_, Integer}
)

```

Call to mark popup as open (don't call every frame!).

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L783).
