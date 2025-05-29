```julia
SetScrollFromPosX(local_x::Real)
SetScrollFromPosX(local_x::Real, center_x_ratio::Real)

```

指定された位置を表示できるようにスクロール量を調整します。一般的には、GetCursorStartPos() + オフセットを使用して有効な位置を計算します。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L448).
