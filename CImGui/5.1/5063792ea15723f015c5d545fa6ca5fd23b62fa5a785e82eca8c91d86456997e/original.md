```julia
IsKeyChordPressed(key_chord::Integer) -> Bool

```

Was key chord (mods + key) pressed, e.g. you can pass 'ImGuiMod*Ctrl | ImGuiKey*S' as a key-chord. This doesn't do any routing or focus check, please consider using Shortcut() function instead.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L1003).
