```
boundingboxes(maxtree::MaxTree) -> Array{NTuple{2, CartesianIndex}}
```

すべての `maxtree` コンポーネントの最小バウンディングボックスを計算します。

# 戻り値

元の画像と同じ形状の配列。`i` 番目の要素は、インデックス `i` の参照ピクセルによって表されるコンポーネントのバウンディングボックスの最小および最大のカートesianインデックスのタプルです。

# 参照

[`diameters`](@ref).
