```julia
SetNextWindowSizeConstraints(
    size_min::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    size_max::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
)
SetNextWindowSizeConstraints(
    size_min::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    size_max::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    custom_callback::Union{Ptr{Nothing}, Base.CFunction}
)
SetNextWindowSizeConstraints(
    size_min::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    size_max::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    custom_callback::Union{Ptr{Nothing}, Base.CFunction},
    custom_callback_data
)

```

次のウィンドウサイズの制限を設定します。制限を設けたくない場合は0.0fまたはFLT_MAXを使用してください。同じ軸の最小値と最大値に-1を使用すると、現在のサイズを保持します（それ自体が制約です）。コールバックを使用して、非自明なプログラム的制約を適用します。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L420).
