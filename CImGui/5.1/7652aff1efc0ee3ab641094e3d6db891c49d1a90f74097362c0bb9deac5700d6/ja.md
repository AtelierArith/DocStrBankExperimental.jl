```julia
IsKeyChordPressed(
    key_chord::Integer,
    flags::Union{CImGui.lib.ImGuiInputFlags_, Integer}
) -> Bool
IsKeyChordPressed(
    key_chord::Integer,
    flags::Union{CImGui.lib.ImGuiInputFlags_, Integer},
    owner_id::Integer
) -> Bool

```

!!! 警告     この関数は内部的なものであり、将来的に変更される可能性があります。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui_internal.h#L3480).
