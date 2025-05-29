既存の要素を`s`で再アクティブ化します。

```julia
activate!(s::SimplexCellList, group_idx::Integer, element_idx::Integer, element_type::Type{Simplex{N}})::Nothing
```

非アクティブな要素はマッピングされません。要素はデフォルトでアクティブです。
