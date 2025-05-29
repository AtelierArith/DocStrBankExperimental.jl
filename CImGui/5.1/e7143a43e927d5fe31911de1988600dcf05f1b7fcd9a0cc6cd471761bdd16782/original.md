```julia
TableGetHoveredColumn() -> Int32

```

Return hovered column. return -1 when table is not hovered. return columns*count if the unused space at the right of visible columns is hovered. Can also use (TableGetColumnFlags() & ImGuiTableColumnFlags*IsHovered) instead.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L857).
