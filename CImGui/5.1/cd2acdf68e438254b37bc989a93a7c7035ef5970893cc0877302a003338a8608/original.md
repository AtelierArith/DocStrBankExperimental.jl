```julia
SetTabItemClosed(tab_or_docked_window_label)

```

Notify TabBar or Docking system of a closed tab/window ahead (useful to reduce visual flicker on reorderable tab bars). For tab-bar: call after BeginTabBar() and before Tab submissions. Otherwise call with a window name.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L878).
