```julia
BeginPopupModal(name) -> Bool
BeginPopupModal(name, p_open) -> Bool
BeginPopupModal(
    name,
    p_open,
    flags::Union{CImGui.lib.ImGuiWindowFlags_, Integer}
) -> Bool

```

モーダルが開いている場合はtrueを返し、出力を開始できます。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L772).
