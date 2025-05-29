```
diameters(maxtree::MaxTree) -> Array{Int}
```

すべての `maxtree` コンポーネントの「直径」を計算します。

*max-tree* 接続コンポーネントの「直径」は、コンポーネントのバウンディングボックスの最も広い側の長さです。

# 戻り値

元の画像と同じ形状の配列。`i` 番目の要素は、インデックス `i` の参照ピクセルによって表されるコンポーネントの「直径」です。

# 参照

[`boundingboxes`](@ref), [`areas`](@ref), [`diameter_opening`](@ref), [`diameter_closing`](@ref).
