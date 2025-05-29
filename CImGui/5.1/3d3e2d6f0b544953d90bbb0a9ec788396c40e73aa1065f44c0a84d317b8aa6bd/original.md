```julia
Draw(self::Ptr{CImGui.lib.ImGuiTextFilter}) -> Bool
Draw(self::Ptr{CImGui.lib.ImGuiTextFilter}, label) -> Bool
Draw(
    self::Ptr{CImGui.lib.ImGuiTextFilter},
    label,
    width
) -> Bool

```

Helper calling InputText+Build.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L2671).
