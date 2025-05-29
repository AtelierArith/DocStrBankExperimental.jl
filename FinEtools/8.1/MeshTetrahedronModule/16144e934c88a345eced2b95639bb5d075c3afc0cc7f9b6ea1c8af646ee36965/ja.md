```
T10layeredplatex(
    xs::VecOrMat{T},
    ys::VecOrMat{T},
    ts::VecOrMat{T},
    nts::VecOrMat{IT},
    orientation::Symbol = :a,
) where {T<:Number, IT<:Integer}
```

指定された面内座標を持つ層状ブロック（複合板）のT10メッシュ。

xs,ys = 各層のノードの位置。ts = 層の厚さの配列、nts = 各層の要素数の配列

各層の有限要素は、下から1から始まる層番号でラベル付けされています。
