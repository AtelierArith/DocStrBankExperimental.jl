```julia
InputInt(label, v) -> Bool
InputInt(label, v, step) -> Bool
InputInt(label, v, step, step_fast) -> Bool
InputInt(
    label,
    v,
    step,
    step_fast,
    flags::Union{CImGui.lib.ImGuiInputTextFlags_, Integer}
) -> Bool

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L647).
