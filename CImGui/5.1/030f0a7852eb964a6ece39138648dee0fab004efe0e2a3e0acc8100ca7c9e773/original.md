```julia
InputTextMultiline(label, buf, buf_size) -> Bool
InputTextMultiline(
    label,
    buf,
    buf_size,
    size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
) -> Bool
InputTextMultiline(
    label,
    buf,
    buf_size,
    size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    flags::Union{CImGui.lib.ImGuiInputTextFlags_, Integer}
) -> Bool
InputTextMultiline(
    label,
    buf,
    buf_size,
    size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    flags::Union{CImGui.lib.ImGuiInputTextFlags_, Integer},
    callback::Union{Ptr{Nothing}, Base.CFunction}
) -> Bool
InputTextMultiline(
    label,
    buf,
    buf_size,
    size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    flags::Union{CImGui.lib.ImGuiInputTextFlags_, Integer},
    callback::Union{Ptr{Nothing}, Base.CFunction},
    user_data
) -> Bool

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L641).
