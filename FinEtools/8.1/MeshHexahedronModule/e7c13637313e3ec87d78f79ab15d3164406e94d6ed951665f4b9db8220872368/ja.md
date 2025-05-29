```
H8layeredplatex(xs::Vector{T}, ys::Vector{T}, ts::Vector{T}, nts::Vector{IT}) where {T<:Number, IT<:Integer}
```

指定された面内座標を持つ層状ブロック（複合板）のH8メッシュ。

xs,ys = 各層のノードの位置。ts = 層の厚さの配列、nts = 各層の要素数の配列

各層の有限要素は、1から始まる層番号でラベル付けされます。
