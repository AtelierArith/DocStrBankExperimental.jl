```julia
BeginPopup(str_id) -> Bool
BeginPopup(
    str_id,
    flags::Union{CImGui.lib.ImGuiWindowFlags_, Integer}
) -> Bool

```

ポップアップが開いている場合はtrueを返し、出力を開始できます。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L771).
