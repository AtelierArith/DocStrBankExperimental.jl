```julia
PathArcToFast(
    self::Ptr{CImGui.lib.ImDrawList},
    center::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    radius,
    a_min_of_12,
    a_max_of_12
)

```

12ステップの円のために事前計算された角度を使用します。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3272).
