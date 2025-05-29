```julia
IsKeyPressed(
    key::CImGui.lib.ImGuiKey,
    flags::Union{CImGui.lib.ImGuiInputFlags_, Integer}
) -> Bool
IsKeyPressed(
    key::CImGui.lib.ImGuiKey,
    flags::Union{CImGui.lib.ImGuiInputFlags_, Integer},
    owner_id::Integer
) -> Bool

```

Important: when transitioning from old to new IsKeyPressed(): old API has "bool repeat = true", so would default to repeat. New API requiress explicit ImGuiInputFlags_Repeat.

!!! warning
    This function is internal, it may change in the future.


[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui_internal.h#L3478).
