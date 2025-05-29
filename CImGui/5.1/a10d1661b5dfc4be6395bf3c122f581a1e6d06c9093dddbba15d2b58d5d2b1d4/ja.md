```julia
BeginMultiSelect(
    flags::Union{CImGui.lib.ImGuiMultiSelectFlags_, Integer}
) -> Ptr{CImGui.lib.ImGuiMultiSelectIO}
BeginMultiSelect(
    flags::Union{CImGui.lib.ImGuiMultiSelectFlags_, Integer},
    selection_size
) -> Ptr{CImGui.lib.ImGuiMultiSelectIO}
BeginMultiSelect(
    flags::Union{CImGui.lib.ImGuiMultiSelectFlags_, Integer},
    selection_size,
    items_count
) -> Ptr{CImGui.lib.ImGuiMultiSelectIO}

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L699).
