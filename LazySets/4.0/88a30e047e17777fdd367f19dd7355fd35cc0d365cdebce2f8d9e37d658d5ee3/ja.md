MinkowskiSumArray{N, S<:LazySet{N}} <: LazySet{N}

有限個の集合のミンコフスキー和を表す型です。

### フィールド

  * `array` – 集合の配列

### ノート

この型は、すべての要素の次元が一致することを前提としています。

`ZeroSet`は中立要素であり、`EmptySet`は`MinkowskiSumArray`の吸収要素です。

ミンコフスキー和は凸性を保持します：集合の引数が凸であれば、それらのミンコフスキー和も凸です。
