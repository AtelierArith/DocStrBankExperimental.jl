既存の要素が `s` の中でアクティブかどうかを返します。

```julia
isActive(s::SimplexCellList, group_idx::Integer, element_idx::Integer, element_type::Type{Simplex{N}})::Bool
```

非アクティブな要素はマッピングされません。要素はデフォルトでアクティブです。
