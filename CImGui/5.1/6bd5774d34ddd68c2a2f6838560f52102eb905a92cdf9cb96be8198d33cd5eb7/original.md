```julia
AddKeyAnalogEvent(
    self::Ptr{CImGui.lib.ImGuiIO},
    key::CImGui.lib.ImGuiKey,
    down,
    v
)

```

Queue a new key down/up event for analog values (e.g. ImGuiKey*Gamepad* values). Dead-zones should be handled by the backend.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L2439).
