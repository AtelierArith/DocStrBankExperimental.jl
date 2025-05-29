```
MinkowskiSum{N, S1<:LazySet{N}, S2<:LazySet{N}} <: LazySet{N}
```

2つの集合のミンコフスキー和を表す型、すなわち集合

$$
X ⊕ Y = \{x + y : x ∈ X, y ∈ Y\}.
$$

### フィールド

  * `X` – 集合
  * `Y` – 集合

### ノート

`ZeroSet`は中立要素であり、`EmptySet`は`MinkowskiSum`の吸収要素です。

ミンコフスキー和は凸性を保持します：集合の引数が凸であれば、それらのミンコフスキー和も凸です。
