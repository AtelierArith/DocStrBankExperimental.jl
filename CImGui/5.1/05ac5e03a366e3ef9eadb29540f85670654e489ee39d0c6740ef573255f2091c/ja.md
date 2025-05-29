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

[Optional] レガシー <1.87 IsKeyXXX() 関数のインデックスを指定し、ネイティブインデックス + ネイティブキーコード、スキャンコードを指定します。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L2450).
