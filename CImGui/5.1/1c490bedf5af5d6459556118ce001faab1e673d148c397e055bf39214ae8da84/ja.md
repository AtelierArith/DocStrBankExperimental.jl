```julia
GetColorU32(
    idx::Union{CImGui.lib.ImGuiCol_, Integer}
) -> UInt32
GetColorU32(
    idx::Union{CImGui.lib.ImGuiCol_, Integer},
    alpha_mul::Real
) -> UInt32

```

スタイルのアルファが適用された指定されたスタイルカラーを取得し、オプションの追加アルファ乗数を適用し、ImDrawListに適した32ビット値としてパックします。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L478).
