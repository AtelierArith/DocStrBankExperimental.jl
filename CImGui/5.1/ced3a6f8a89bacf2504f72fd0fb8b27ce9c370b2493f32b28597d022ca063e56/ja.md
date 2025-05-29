```julia
GetNextSelectedItem(
    self::Ptr{CImGui.lib.ImGuiSelectionBasicStorage},
    opaque_it,
    out_id::Union{Ptr{Nothing}, Ref{Integer}, Ref{UInt32}}
) -> Bool

```

選択を反復処理するには、'void* it = NULL; ImGuiID id; while (selection.GetNextSelectedItem(&it, &id))  ... '。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3031).
