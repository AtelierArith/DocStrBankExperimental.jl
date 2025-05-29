```julia
SetNextWindowSizeConstraints(
    size_min::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    size_max::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
)
SetNextWindowSizeConstraints(
    size_min::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    size_max::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    custom_callback::Union{Ptr{Nothing}, Base.CFunction}
)
SetNextWindowSizeConstraints(
    size_min::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    size_max::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    custom_callback::Union{Ptr{Nothing}, Base.CFunction},
    custom_callback_data
)

```

Set next window size limits. use 0.0f or FLT_MAX if you don't want limits. Use -1 for both min and max of same axis to preserve current size (which itself is a constraint). Use callback to apply non-trivial programmatic constraints.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L420).
