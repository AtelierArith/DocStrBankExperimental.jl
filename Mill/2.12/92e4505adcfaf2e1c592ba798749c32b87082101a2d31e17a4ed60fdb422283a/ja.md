```
removeinstances(n::AbstractBagNode, mask)
```

`mask`を使用して`n`からインスタンスを削除し、バッグインデックスを適切に再マッピングします。

# 例

```jldoctest
julia> b1 = BagNode(ArrayNode([1 2 3; 4 5 6]), bags([1:2, 0:-1, 3:3]))
BagNode  3 obs
  ╰── ArrayNode(2×3 Array with Int64 elements)  3 obs

julia> b2 = removeinstances(b1, [false, true, true])
BagNode  3 obs
  ╰── ArrayNode(2×2 Array with Int64 elements)  2 obs

julia> b2.data
2×2 ArrayNode{Matrix{Int64}, Nothing}:
 2  3
 5  6

julia> b2.bags
AlignedBags{Int64}(UnitRange{Int64}[1:1, 0:-1, 2:2])
```
