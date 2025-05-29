```julia
AddKeyEvent(
    self::Ptr{CImGui.lib.ImGuiIO},
    key::CImGui.lib.ImGuiKey,
    down
)

```

Queue a new key down/up event. Key should be "translated" (as in, generally ImGuiKey_A matches the key end-user would use to emit an 'A' character).

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L2438).
