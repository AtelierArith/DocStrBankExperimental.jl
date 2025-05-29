```julia
CollapsingHeader(
    label::Union{Ptr{Int8}, Ptr{Nothing}, String}
) -> Bool
CollapsingHeader(
    label::Union{Ptr{Int8}, Ptr{Nothing}, String},
    flags::Union{CImGui.lib.ImGuiTreeNodeFlags_, Integer}
) -> Bool

```

If returning 'true' the header is open. doesn't indent nor push on ID stack. user doesn't have to call TreePop().

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L681).
