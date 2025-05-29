```julia
ApplyRequests(
    self::Ptr{CImGui.lib.ImGuiSelectionBasicStorage},
    ms_io::Union{Ptr{Nothing}, Ref{CImGui.lib.ImGuiMultiSelectIO}}
)

```

Apply selection requests coming from BeginMultiSelect() and EndMultiSelect() functions. It uses 'items_count' passed to BeginMultiSelect().

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3026).
