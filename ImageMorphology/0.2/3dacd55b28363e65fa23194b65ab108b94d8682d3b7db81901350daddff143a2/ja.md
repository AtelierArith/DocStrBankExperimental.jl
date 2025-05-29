```
areas(maxtree::MaxTree) -> Array{Int}
```

すべての `maxtree` コンポーネントの面積を計算します。

# 戻り値

元の画像と同じ形状の配列。`i` 番目の要素は、インデックス `i` の参照ピクセルによって表されるコンポーネントの面積（ピクセル単位）です。

# 参照

[`diameters`](@ref), [`area_opening`](@ref), [`area_closing`](@ref).
