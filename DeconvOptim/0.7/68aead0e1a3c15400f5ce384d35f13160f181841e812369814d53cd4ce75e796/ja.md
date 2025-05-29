```
center_extract(arr, new_size_array)
```

配列の中心を抽出します。 `new_size_array` は各次元の出力サイズを示すサイズのリストでなければなりません。中心とは、中心周波数が中心位置に留まることを意味します。偶数および奇数の両方に対応しています。 `length(new_size_array) < length(ndims(arr))` の場合、残りの次元は変更されずにコピーされます。

# 例

```jldoctest
julia> DeconvOptim.center_extract([1 2; 3 4], [1]) 
1×2 Array{Int64,2}:
 3  4
julia> DeconvOptim.center_extract([1 2; 3 4], [1, 1])
1×1 Array{Int64,2}:
 4
julia> DeconvOptim.center_extract([1 2 3; 3 4 5; 6 7 8], [2 2])
2×2 Array{Int64,2}:
 1  2
 3  4
```
