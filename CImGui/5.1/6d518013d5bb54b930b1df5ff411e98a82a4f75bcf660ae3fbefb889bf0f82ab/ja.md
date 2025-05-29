```julia
ApplyRequests(
    self::Ptr{CImGui.lib.ImGuiSelectionBasicStorage},
    ms_io::Union{Ptr{Nothing}, Ref{CImGui.lib.ImGuiMultiSelectIO}}
)

```

BeginMultiSelect() および EndMultiSelect() 関数からの選択リクエストを適用します。これは、BeginMultiSelect() に渡された 'items_count' を使用します。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3026).
