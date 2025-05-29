```julia
AddMouseWheelEvent(
    self::Ptr{CImGui.lib.ImGuiIO},
    wheel_x,
    wheel_y
)

```

Queue a mouse wheel update. wheel*y<0: scroll down, wheel*y>0: scroll up, wheel*x<0: scroll right, wheel*x>0: scroll left.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L2442).
