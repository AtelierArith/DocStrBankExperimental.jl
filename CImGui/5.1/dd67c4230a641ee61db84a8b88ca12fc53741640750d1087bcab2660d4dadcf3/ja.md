```julia
SetScrollHereX()
SetScrollHereX(center_x_ratio)

```

現在のカーソル位置を表示するためにスクロール量を調整します。 center*x*ratio=0.0: 左, 0.5: 中央, 1.0: 右。 "デフォルト/現在のアイテム" を表示するために使用する場合は、代わりに SetItemDefaultFocus() を使用することを検討してください。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L446).
