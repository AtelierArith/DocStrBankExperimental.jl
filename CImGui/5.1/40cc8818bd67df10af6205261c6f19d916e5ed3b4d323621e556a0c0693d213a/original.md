```julia
IsMouseClicked(
    button::Union{CImGui.lib.ImGuiMouseButton_, Integer},
    flags::Union{CImGui.lib.ImGuiInputFlags_, Integer}
) -> Bool
IsMouseClicked(
    button::Union{CImGui.lib.ImGuiMouseButton_, Integer},
    flags::Union{CImGui.lib.ImGuiInputFlags_, Integer},
    owner_id::Integer
) -> Bool

```

!!! warning
    This function is internal, it may change in the future.


[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui_internal.h#L3482).
