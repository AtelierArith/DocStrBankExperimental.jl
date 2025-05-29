```julia
SetWindowSize(
    name::Union{Ptr{Int8}, String},
    size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
)
SetWindowSize(
    name::Union{Ptr{Int8}, String},
    size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    cond::Union{CImGui.lib.ImGuiCond_, Integer}
)

```

名前付きウィンドウのサイズを設定します。この軸で自動フィットを強制するには、軸を0.0fに設定します。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L433).
