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

Change the color of a cell, row, or column. See ImGuiTableBgTarget_ flags for details.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L858).
