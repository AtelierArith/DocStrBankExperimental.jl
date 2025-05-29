```julia
TableGetSortSpecs() -> Ptr{CImGui.lib.ImGuiTableSortSpecs}

```

Get latest sort specs for the table (NULL if not sorting).  Lifetime: don't hold on this pointer over multiple frames or past any subsequent call to BeginTable().

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L850).
