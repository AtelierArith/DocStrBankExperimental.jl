```julia
TableGetHoveredColumn() -> Int32

```

ホバーされた列を返します。テーブルがホバーされていない場合は -1 を返します。可視列の右側の未使用スペースがホバーされている場合は columns*count を返します。代わりに (TableGetColumnFlags() & ImGuiTableColumnFlags*IsHovered) を使用することもできます。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L857).
