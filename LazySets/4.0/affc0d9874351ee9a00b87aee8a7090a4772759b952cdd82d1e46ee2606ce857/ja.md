UnionSetArray{N, S<:LazySet{N}} <: LazySet{N}

有限個の集合の和集合を表す型です。

### フィールド

  * `array` – 集合の配列

### 注意事項

凸集合の和集合は通常、凸ではありません。
