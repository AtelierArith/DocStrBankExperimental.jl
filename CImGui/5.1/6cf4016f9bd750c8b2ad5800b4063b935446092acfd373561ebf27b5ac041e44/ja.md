```julia
BeginPopupContextVoid() -> Bool
BeginPopupContextVoid(str_id) -> Bool
BeginPopupContextVoid(
    str_id,
    popup_flags::Union{CImGui.lib.ImGuiPopupFlags_, Integer}
) -> Bool

```

クリックしたときに無の領域（ウィンドウがない場所）でポップアップを開いて開始します。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L795).
