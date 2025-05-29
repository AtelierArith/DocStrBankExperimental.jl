```julia
TabItemButton(label) -> Bool
TabItemButton(
    label,
    flags::Union{CImGui.lib.ImGuiTabItemFlags_, Integer}
) -> Bool

```

Create a Tab behaving like a button. return true when clicked. cannot be selected in the tab bar.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L877).
