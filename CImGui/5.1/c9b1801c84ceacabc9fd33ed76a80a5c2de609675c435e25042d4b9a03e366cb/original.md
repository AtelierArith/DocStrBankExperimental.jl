```julia
DockSpace(dockspace_id::Integer) -> UInt32
DockSpace(
    dockspace_id::Integer,
    size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T}
) -> UInt32
DockSpace(
    dockspace_id::Integer,
    size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    flags::Union{CImGui.lib.ImGuiDockNodeFlags_, Integer}
) -> UInt32
DockSpace(
    dockspace_id::Integer,
    size::Union{CImGui.lib.ImVec2, Tuple{T, T} where T},
    flags::Union{CImGui.lib.ImGuiDockNodeFlags_, Integer},
    window_class::Union{Ptr{Nothing}, Ref{CImGui.lib.ImGuiWindowClass}}
) -> UInt32

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L893).
