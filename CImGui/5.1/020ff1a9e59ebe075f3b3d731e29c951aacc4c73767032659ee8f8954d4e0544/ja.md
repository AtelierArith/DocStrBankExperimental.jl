```julia
GetColorU32(
    col::Union{CImGui.lib.ImVec4, NTuple{4, T} where T}
) -> UInt32

```

スタイルのアルファが適用された指定された色を取得し、ImDrawListに適した32ビット値としてパックします。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L479).
