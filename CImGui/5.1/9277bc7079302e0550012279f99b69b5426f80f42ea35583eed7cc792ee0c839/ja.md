```julia
SetWindowPos(
    pos::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
)
SetWindowPos(
    pos::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    cond::Union{CImGui.lib.ImGuiCond_, Integer}
)

```

（推奨されません）現在のウィンドウ位置を設定します - Begin()/End()内で呼び出します。SetNextWindowPos()の使用を推奨します。これにより、ティアリングや副作用が発生する可能性があります。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L427).
