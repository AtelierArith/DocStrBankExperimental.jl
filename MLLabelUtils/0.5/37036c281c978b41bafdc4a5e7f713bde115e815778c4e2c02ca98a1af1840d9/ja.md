```
labelmap!(dict, idx, elem) -> Dict
```

与えられたラベルマップ `dict` を新しい要素 `elem` で更新します。`elem` はインデックス `idx` に関連付けられていると仮定されます。

```
julia> lm = labelmap([0, 1, 1, 0, 0])
Dict{Int64,Array{Int64,1}} with 2 entries:
  0 => [1,4,5]
  1 => [2,3]

julia> labelmap!(lm, 6, 0)
Dict{Int64,Array{Int64,1}} with 2 entries:
  0 => [1,4,5,6]
  1 => [2,3]

julia> labelmap!(lm, 7:8, [1,0])
Dict{Int64,Array{Int64,1}} with 2 entries:
  0 => [1,4,5,6,8]
  1 => [2,3,7]
```
