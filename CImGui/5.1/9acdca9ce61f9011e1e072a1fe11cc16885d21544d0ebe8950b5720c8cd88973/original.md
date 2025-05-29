```julia
InputDouble(label, v) -> Bool
InputDouble(label, v, step) -> Bool
InputDouble(label, v, step, step_fast) -> Bool
InputDouble(label, v, step, step_fast, format) -> Bool
InputDouble(
    label,
    v,
    step,
    step_fast,
    format,
    flags::Union{CImGui.lib.ImGuiInputTextFlags_, Integer}
) -> Bool

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L651).
