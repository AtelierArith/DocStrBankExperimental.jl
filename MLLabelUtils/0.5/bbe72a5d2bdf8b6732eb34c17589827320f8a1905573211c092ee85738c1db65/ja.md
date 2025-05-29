```
labelmap(obj) -> Dict
```

`obj`内のラベルから、そのラベルに対応する`obj`内のすべての個別要素インデックスへのマッピングを計算します。

```
julia> labelmap([0, 1, 1, 0, 0])
Dict{Int64,Array{Int64,1}} with 2 entries:
  0 => [1,4,5]
  1 => [2,3]
```
