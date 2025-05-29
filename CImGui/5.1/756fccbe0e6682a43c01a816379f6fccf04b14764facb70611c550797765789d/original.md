```julia
SetNextWindowContentSize(
    size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
)

```

Set next window content size (~ scrollable client area, which enforce the range of scrollbars). Not including window decorations (title bar, menu bar, etc.) nor WindowPadding. set an axis to 0.0f to leave it automatic. call before Begin().

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L421).
