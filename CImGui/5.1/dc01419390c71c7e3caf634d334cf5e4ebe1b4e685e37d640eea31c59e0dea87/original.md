```julia
TableGetColumnName() -> Ptr{Int8}
TableGetColumnName(column_n::Integer) -> Ptr{Int8}

```

Return "" if column didn't have a name declared by TableSetupColumn(). Pass -1 to use current column.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L854).
