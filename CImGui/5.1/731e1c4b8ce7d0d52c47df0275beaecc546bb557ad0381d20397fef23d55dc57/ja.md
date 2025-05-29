```julia
SetWindowCollapsed(collapsed::Bool)
SetWindowCollapsed(
    collapsed::Bool,
    cond::Union{CImGui.lib.ImGuiCond_, Integer}
)

```

(推奨されません) 現在のウィンドウの折りたたみ状態を設定します。SetNextWindowCollapsed()の使用を推奨します。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L429).
