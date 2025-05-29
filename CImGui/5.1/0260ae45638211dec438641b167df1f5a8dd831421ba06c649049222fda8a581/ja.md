```julia
InputText(label, buf, buf_size) -> Bool
InputText(
    label,
    buf,
    buf_size,
    flags::Union{CImGui.lib.ImGuiInputTextFlags_, Integer}
) -> Bool
InputText(
    label,
    buf,
    buf_size,
    flags::Union{CImGui.lib.ImGuiInputTextFlags_, Integer},
    callback::Union{Ptr{Nothing}, Base.CFunction}
) -> Bool
InputText(
    label,
    buf,
    buf_size,
    flags::Union{CImGui.lib.ImGuiInputTextFlags_, Integer},
    callback::Union{Ptr{Nothing}, Base.CFunction},
    user_data
) -> Bool

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L640).
