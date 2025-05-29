```julia
TableGetColumnFlags() -> Int32
TableGetColumnFlags(column_n) -> Int32

```

Return column flags so you can query their Enabled/Visible/Sorted/Hovered status flags. Pass -1 to use current column.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L855).
