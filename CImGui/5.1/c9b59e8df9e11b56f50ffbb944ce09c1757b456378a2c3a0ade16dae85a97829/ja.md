```julia
TableGetSortSpecs() -> Ptr{CImGui.lib.ImGuiTableSortSpecs}

```

テーブルの最新のソート仕様を取得します（ソートしていない場合はNULL）。 ライフタイム：このポインタを複数のフレームにわたって保持したり、BeginTable()へのその後の呼び出しを超えて保持しないでください。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L850).
