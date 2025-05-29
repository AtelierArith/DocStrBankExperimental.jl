```julia
SetTabItemClosed(tab_or_docked_window_label)

```

タブ/ウィンドウが閉じられたことをTabBarまたはドッキングシステムに通知します（再配置可能なタブバーでの視覚的なちらつきを減らすのに便利です）。タブバーの場合：BeginTabBar()の後、タブの提出の前に呼び出します。それ以外の場合は、ウィンドウ名を指定して呼び出します。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L878).
