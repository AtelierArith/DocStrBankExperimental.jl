```
ConvexHullArray{N, S<:LazySet{N}} <: ConvexSet{N}
```

有限個の集合の象徴的な凸包を表す型です。

### フィールド

  * `array` – 集合の配列

### 注意事項

`EmptySet`は`ConvexHullArray`の中立要素です。

`ConvexHullArray`は常に凸です。

### 例

100個の二次元ボールの凸包で、中心が正弦波に従う:

```jldoctest
julia> b = [Ball2([2*pi*i/100, sin(2*pi*i/100)], 0.05) for i in 1:100];

julia> c = ConvexHullArray(b);
```
