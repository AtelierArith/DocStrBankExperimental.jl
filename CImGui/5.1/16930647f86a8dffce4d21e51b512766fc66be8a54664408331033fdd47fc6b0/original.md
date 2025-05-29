```julia
SetAppAcceptingEvents(
    self::Ptr{CImGui.lib.ImGuiIO},
    accepting_events
)

```

Set master flag for accepting key/mouse/text events (default to true). Useful if you have native dialog boxes that are interrupting your application loop/refresh, and you want to disable events being queued while your app is frozen.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L2451).
