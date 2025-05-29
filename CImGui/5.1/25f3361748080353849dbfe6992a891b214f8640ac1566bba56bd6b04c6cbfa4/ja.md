```julia
GetColumnOffset() -> Float32
GetColumnOffset(column_index) -> Float32

```

列の位置を取得します（ピクセル単位で、コンテンツ領域の左側から）。現在の列を使用するには-1を渡し、それ以外の場合は0..GetColumnsCount()を含めて指定します。列0は通常0.0fです。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L867).
