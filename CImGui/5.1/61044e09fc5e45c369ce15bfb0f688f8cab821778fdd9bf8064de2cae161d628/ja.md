```julia
IsKeyPressed(
    key::CImGui.lib.ImGuiKey,
    flags::Union{CImGui.lib.ImGuiInputFlags_, Integer}
) -> Bool
IsKeyPressed(
    key::CImGui.lib.ImGuiKey,
    flags::Union{CImGui.lib.ImGuiInputFlags_, Integer},
    owner_id::Integer
) -> Bool

```

重要: 古い IsKeyPressed() から新しい IsKeyPressed() への移行時には、古い API には "bool repeat = true" があり、デフォルトで繰り返しになります。新しい API では明示的に ImGuiInputFlags_Repeat が必要です。

!!! 警告     この関数は内部的なものであり、将来的に変更される可能性があります。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui_internal.h#L3478).
