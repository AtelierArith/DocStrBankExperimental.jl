```
remove_duplicate_sequences(Z::Matrix{Ti}) where Ti<:Integer
```

アライメント行列 `Z` から重複する列を削除します

# 例

```
julia> Z = [1 2 3 1;
            1 3 2 1;]
2×4 Array{Int64,2}:
 1  2  3  1
 1  3  2  1

julia> remove_duplicate_sequences(Z)
重複する列を削除しています... 完了: 4 -> 3
([1 2 3; 1 3 2], [1, 2, 3])
```
