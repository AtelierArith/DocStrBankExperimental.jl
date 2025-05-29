```julia
InputFloat(label, v) -> Bool
InputFloat(label, v, step) -> Bool
InputFloat(label, v, step, step_fast) -> Bool
InputFloat(label, v, step, step_fast, format) -> Bool
InputFloat(
    label,
    v,
    step,
    step_fast,
    format,
    flags::Union{CImGui.lib.ImGuiInputTextFlags_, Integer}
) -> Bool

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L643).
