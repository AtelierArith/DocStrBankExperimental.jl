```
convex_hull(X::LazySet, Y::LazySet)
```

二つの集合の（和集合の）凸包を計算します。

### 入力

  * `X` – 集合
  * `Y` – 集合

### 出力

$$
X ∪ Y
$$

の凸包を表す集合。

### 注意事項

単一の集合の凸包については [`convex_hull(::LazySet)`](@ref) を参照してください。
