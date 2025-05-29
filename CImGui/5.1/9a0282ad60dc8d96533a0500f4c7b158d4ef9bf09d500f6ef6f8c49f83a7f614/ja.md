```julia
SetWindowCollapsed(
    name::Union{Ptr{Int8}, String},
    collapsed::Bool
)
SetWindowCollapsed(
    name::Union{Ptr{Int8}, String},
    collapsed::Bool,
    cond::Union{CImGui.lib.ImGuiCond_, Integer}
)

```

名前付きウィンドウの折りたたみ状態を設定します。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L434).
