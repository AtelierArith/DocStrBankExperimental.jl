```julia
GetColumnOffset() -> Float32
GetColumnOffset(column_index) -> Float32

```

Get position of column line (in pixels, from the left side of the contents region). pass -1 to use current column, otherwise 0..GetColumnsCount() inclusive. column 0 is typically 0.0f.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L867).
