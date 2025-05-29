```julia
RenderPlatformWindowsDefault()
RenderPlatformWindowsDefault(platform_render_arg)
RenderPlatformWindowsDefault(
    platform_render_arg,
    renderer_render_arg
)

```

Call in main loop. will call RenderWindow/SwapBuffers platform functions for each secondary viewport which doesn't have the ImGuiViewportFlags_Minimized flag set. May be reimplemented by user for custom rendering needs.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L1094).
