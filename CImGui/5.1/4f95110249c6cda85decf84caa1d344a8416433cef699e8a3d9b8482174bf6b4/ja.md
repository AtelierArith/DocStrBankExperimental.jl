```julia
SetNextWindowSize(
    size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
)
SetNextWindowSize(
    size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    cond::Union{CImGui.lib.ImGuiCond_, Integer}
)

```

次のウィンドウサイズを設定します。自動フィットを強制するには、この軸に対して0.0fに設定します。Begin()の前に呼び出してください。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L419).
