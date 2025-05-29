```julia
BeginChild(
    str_id::Union{Ptr{Int8}, Ptr{Nothing}, String}
) -> Bool
BeginChild(
    str_id::Union{Ptr{Int8}, Ptr{Nothing}, String},
    size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
) -> Bool
BeginChild(
    str_id::Union{Ptr{Int8}, Ptr{Nothing}, String},
    size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    child_flags::Union{CImGui.lib.ImGuiChildFlags_, Integer}
) -> Bool
BeginChild(
    str_id::Union{Ptr{Int8}, Ptr{Nothing}, String},
    size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    child_flags::Union{CImGui.lib.ImGuiChildFlags_, Integer},
    window_flags::Union{CImGui.lib.ImGuiWindowFlags_, Integer}
) -> Bool

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L398).
