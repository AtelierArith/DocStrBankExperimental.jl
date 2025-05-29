```julia
AddKeyAnalogEvent(
    self::Ptr{CImGui.lib.ImGuiIO},
    key::CImGui.lib.ImGuiKey,
    down,
    v
)

```

アナログ値（例：ImGuiKey*Gamepad*値）のための新しいキーの押下/解放イベントをキューに追加します。デッドゾーンはバックエンドによって処理されるべきです。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L2439).
