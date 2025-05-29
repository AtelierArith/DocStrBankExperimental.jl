```julia
ScaleClipRects(
    self::Ptr{CImGui.lib.ImDrawData},
    fb_scale::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
)

```

各ImDrawCmdのClipRectフィールドをスケーリングするためのヘルパー。最終出力バッファがDear ImGuiが期待するスケールとは異なる場合や、ウィンドウ解像度とフレームバッファ解像度の間に違いがある場合に使用します。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3356).
