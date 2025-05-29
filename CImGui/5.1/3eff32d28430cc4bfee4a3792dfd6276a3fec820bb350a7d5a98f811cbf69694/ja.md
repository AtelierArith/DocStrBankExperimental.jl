```julia
TableSetBgColor(
    target::Union{CImGui.lib.ImGuiTableBgTarget_, Integer},
    color::Integer
)
TableSetBgColor(
    target::Union{CImGui.lib.ImGuiTableBgTarget_, Integer},
    color::Integer,
    column_n
)

```

セル、行、または列の色を変更します。詳細については、ImGuiTableBgTarget_ フラグを参照してください。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L858).
