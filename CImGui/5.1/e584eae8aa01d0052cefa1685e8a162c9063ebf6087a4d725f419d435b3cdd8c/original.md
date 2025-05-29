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

Render-level scissoring. This is passed down to your render function but not used for CPU-side coarse clipping. Prefer using higher-level ImGui::PushClipRect() to affect logic (hit-testing and widget culling).

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3213).
