```
distance_matrix(tree::AbstractPhyloTree, [indices::Vector{<:Integer}])
```

`tree`上のすべてのインデックス間のペアワイズ距離を`AxisArray`として返します。インデックスが指定されていない場合は、すべての葉が入力として使用されます。
