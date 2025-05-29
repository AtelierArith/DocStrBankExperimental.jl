```julia
BeginPopup(str_id) -> Bool
BeginPopup(
    str_id,
    flags::Union{CImGui.lib.ImGuiWindowFlags_, Integer}
) -> Bool

```

Return true if the popup is open, and you can start outputting to it.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L771).
