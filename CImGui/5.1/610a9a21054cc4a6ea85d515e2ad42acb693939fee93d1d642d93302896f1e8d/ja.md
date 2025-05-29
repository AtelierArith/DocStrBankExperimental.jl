```julia
SetWindowSize(
    size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
)
SetWindowSize(
    size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    cond::Union{CImGui.lib.ImGuiCond_, Integer}
)

```

（推奨されません）現在のウィンドウサイズを設定します - Begin()/End()内で呼び出します。自動フィットを強制するにはImVec2(0, 0)に設定します。SetNextWindowSize()の使用を推奨します。これにより、ティアリングや軽微な副作用が発生する可能性があります。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L428).
