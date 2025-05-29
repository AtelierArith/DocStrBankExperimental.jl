```julia
ScaleClipRects(
    self::Ptr{CImGui.lib.ImDrawData},
    fb_scale::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
)

```

Helper to scale the ClipRect field of each ImDrawCmd. Use if your final output buffer is at a different scale than Dear ImGui expects, or if there is a difference between your window resolution and framebuffer resolution.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3356).
