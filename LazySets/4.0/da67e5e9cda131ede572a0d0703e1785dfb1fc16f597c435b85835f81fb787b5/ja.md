```
IntersectionArray{N, S<:LazySet{N}} <: LazySet{N}
```

有限個の集合の交差を表す型です。

### フィールド

  * `array` – 集合の配列

### ノート

この型は、すべての要素の次元が一致することを前提としています。

`EmptySet`は`IntersectionArray`の吸収要素です。

交差は凸性を保持します：集合の引数が凸であれば、その交差も凸です。
