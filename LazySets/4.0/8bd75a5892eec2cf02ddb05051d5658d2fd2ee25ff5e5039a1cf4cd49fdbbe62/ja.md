```
CartesianProductArray{N, S<:LazySet{N}} <: LazySet{N}
```

有限個の集合の直積を表す型です。

### フィールド

  * `array` – 集合の配列

### 注意事項

直積は凸性を保持します：集合の引数が凸であれば、その直積も凸です。
