```julia
AddDrawList(
    self::Ptr{CImGui.lib.ImDrawData},
    draw_list::Union{Ptr{Nothing}, Ref{CImGui.lib.ImDrawList}}
)

```

既存のImDrawDataに外部描画リストを追加するためのヘルパーです。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3354).
