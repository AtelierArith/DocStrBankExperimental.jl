```julia
SetNextWindowPos(
    pos::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
)
SetNextWindowPos(
    pos::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    cond::Union{CImGui.lib.ImGuiCond_, Integer}
)
SetNextWindowPos(
    pos::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    cond::Union{CImGui.lib.ImGuiCond_, Integer},
    pivot::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
)

```

次のウィンドウの位置を設定します。Begin()の前に呼び出します。pivot=(0.5f,0.5f)を使用して指定した点を中心にするなどします。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L418).
