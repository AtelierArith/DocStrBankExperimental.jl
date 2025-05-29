```julia
IsWindowFocused() -> Bool
IsWindowFocused(
    flags::Union{CImGui.lib.ImGuiFocusedFlags_, Integer}
) -> Bool

```

Is current window focused? or its root/child, depending on flags. see flags for options.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L406).
