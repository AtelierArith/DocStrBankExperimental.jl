```julia
AddMouseWheelEvent(
    self::Ptr{CImGui.lib.ImGuiIO},
    wheel_x,
    wheel_y
)

```

マウスホイールの更新をキューに追加します。wheel*y<0: 下にスクロール、wheel*y>0: 上にスクロール、wheel*x<0: 右にスクロール、wheel*x>0: 左にスクロール。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L2442).
