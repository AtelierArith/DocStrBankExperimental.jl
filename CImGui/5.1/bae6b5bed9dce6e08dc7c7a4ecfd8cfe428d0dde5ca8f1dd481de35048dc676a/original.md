```julia
DockSpaceOverViewport() -> UInt32
DockSpaceOverViewport(dockspace_id::Integer) -> UInt32
DockSpaceOverViewport(
    dockspace_id::Integer,
    viewport::Union{Ptr{Nothing}, Ref{CImGui.lib.ImGuiViewport}}
) -> UInt32
DockSpaceOverViewport(
    dockspace_id::Integer,
    viewport::Union{Ptr{Nothing}, Ref{CImGui.lib.ImGuiViewport}},
    flags::Union{CImGui.lib.ImGuiDockNodeFlags_, Integer}
) -> UInt32
DockSpaceOverViewport(
    dockspace_id::Integer,
    viewport::Union{Ptr{Nothing}, Ref{CImGui.lib.ImGuiViewport}},
    flags::Union{CImGui.lib.ImGuiDockNodeFlags_, Integer},
    window_class::Union{Ptr{Nothing}, Ref{CImGui.lib.ImGuiWindowClass}}
) -> UInt32

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L894).
