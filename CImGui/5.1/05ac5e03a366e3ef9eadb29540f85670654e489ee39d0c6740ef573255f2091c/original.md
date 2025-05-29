```julia
SetKeyEventNativeData(
    self::Ptr{CImGui.lib.ImGuiIO},
    key::CImGui.lib.ImGuiKey,
    native_keycode,
    native_scancode
)
SetKeyEventNativeData(
    self::Ptr{CImGui.lib.ImGuiIO},
    key::CImGui.lib.ImGuiKey,
    native_keycode,
    native_scancode,
    native_legacy_index
)

```

[Optional] Specify index for legacy <1.87 IsKeyXXX() functions with native indices + specify native keycode, scancode.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L2450).
