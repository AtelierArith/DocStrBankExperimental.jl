`s`に新しい要素を追加し、その要素のインデックスを返します：

```julia
addElement!(s::SimplexCellList, group_idx::Integer, element::Simplex{N})::Int32
```

新しい要素は指定されたグループの末尾に追加されます。
