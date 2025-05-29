```julia
PushClipRect(
    self::Ptr{CImGui.lib.ImDrawList},
    clip_rect_min::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    clip_rect_max::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
)
PushClipRect(
    self::Ptr{CImGui.lib.ImDrawList},
    clip_rect_min::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    clip_rect_max::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    intersect_with_current_clip_rect
)

```

レンダーレベルのクリッピング。これはあなたのレンダリング関数に渡されますが、CPU側の粗いクリッピングには使用されません。ロジック（ヒットテストとウィジェットのカリング）に影響を与えるためには、より高レベルのImGui::PushClipRect()を使用することをお勧めします。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3213).
