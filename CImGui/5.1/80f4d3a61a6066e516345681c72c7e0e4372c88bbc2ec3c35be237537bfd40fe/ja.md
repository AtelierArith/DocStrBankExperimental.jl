```julia
OpenPopupOnItemClick()
OpenPopupOnItemClick(str_id)
OpenPopupOnItemClick(
    str_id,
    popup_flags::Union{CImGui.lib.ImGuiPopupFlags_, Integer}
)

```

最後のアイテムがクリックされたときにポップアップを開くためのヘルパー。デフォルトは ImGuiPopupFlags*MouseButtonRight == 1 に設定されています。（注：ポップアップの動作と一貫性を持たせるために、実際にはマウス _released* イベントでトリガーされます）。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L785).
