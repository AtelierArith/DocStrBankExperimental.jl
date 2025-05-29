```
symmetric_interval_hull(S::LazySet{N}) where {N}
```

原点を中心としたタイトなハイパーレクタングルによって集合を過大評価します。

### 入力

  * `S` – 集合

### 出力

原点に対して中心対称なタイトなハイパーレクタングル。

### 注意事項

この関数の別名は `box_approximation_symmetric` です。

### アルゴリズム

ボックスの中心は原点であり、半径は `extrema` 関数を介して取得されます。
