```julia
IsKeyPressed(key::CImGui.lib.ImGuiKey) -> Bool
IsKeyPressed(key::CImGui.lib.ImGuiKey, repeat::Bool) -> Bool

```

キーが押されましたか（!DownからDownに移行しましたか）？ repeat=trueの場合、io.KeyRepeatDelay / KeyRepeatRateを使用します。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L1001).
