```julia
AddMouseViewportEvent(
    self::Ptr{CImGui.lib.ImGuiIO},
    id::Integer
)

```

Queue a mouse hovered viewport. Requires backend to set ImGuiBackendFlags_HasMouseHoveredViewport to call this (for multi-viewport support).

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L2444).
