```julia
SetScrollHereY()
SetScrollHereY(center_y_ratio)

```

Adjust scrolling amount to make current cursor position visible. center*y*ratio=0.0: top, 0.5: center, 1.0: bottom. When using to make a "default/current item" visible, consider using SetItemDefaultFocus() instead.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L447).
