```julia
SetScrollFromPosY(local_y::Real)
SetScrollFromPosY(local_y::Real, center_y_ratio::Real)

```

指定された位置を表示可能にするためにスクロール量を調整します。一般的には、GetCursorStartPos() + オフセットを使用して有効な位置を計算します。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L449).
