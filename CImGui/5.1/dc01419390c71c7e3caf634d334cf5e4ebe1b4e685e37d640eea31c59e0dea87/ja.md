```julia
TableGetColumnName() -> Ptr{Int8}
TableGetColumnName(column_n::Integer) -> Ptr{Int8}

```

列にTableSetupColumn()によって宣言された名前がない場合は""を返します。現在の列を使用するには-1を渡してください。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L854).
