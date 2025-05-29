```julia
IsKeyPressed(key::CImGui.lib.ImGuiKey) -> Bool
IsKeyPressed(key::CImGui.lib.ImGuiKey, repeat::Bool) -> Bool

```

Was key pressed (went from !Down to Down)? if repeat=true, uses io.KeyRepeatDelay / KeyRepeatRate.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L1001).
