`s`内の既存の要素を非アクティブにします。

```julia
deactivate!(s::SimplexCellList, group_idx::Integer, element_idx::Integer, element_type::Type{Simplex{N}})::Nothing
```

非アクティブな要素はマッピングされません。要素はデフォルトでアクティブです。
