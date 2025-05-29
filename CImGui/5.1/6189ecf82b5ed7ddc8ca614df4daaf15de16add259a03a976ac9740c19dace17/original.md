```julia
BeginTabItem(label) -> Bool
BeginTabItem(label, p_open) -> Bool
BeginTabItem(
    label,
    p_open,
    flags::Union{CImGui.lib.ImGuiTabItemFlags_, Integer}
) -> Bool

```

Create a Tab. Returns true if the Tab is selected.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L875).
