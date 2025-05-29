```julia
BeginTabItem(label) -> Bool
BeginTabItem(label, p_open) -> Bool
BeginTabItem(
    label,
    p_open,
    flags::Union{CImGui.lib.ImGuiTabItemFlags_, Integer}
) -> Bool

```

タブを作成します。タブが選択されている場合はtrueを返します。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L875).
