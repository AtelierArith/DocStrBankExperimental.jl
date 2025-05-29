```julia
BeginPopupModal(name) -> Bool
BeginPopupModal(name, p_open) -> Bool
BeginPopupModal(
    name,
    p_open,
    flags::Union{CImGui.lib.ImGuiWindowFlags_, Integer}
) -> Bool

```

Return true if the modal is open, and you can start outputting to it.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L772).
