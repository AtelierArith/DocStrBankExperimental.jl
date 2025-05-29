```
difference(X::LazySet, Y::LazySet)
```

二つの集合の差を計算します。

### 入力

  * `X` – 集合
  * `Y` – 集合

### 出力

差を表す集合 $X ∖ Y$。

### 注意事項

集合の差は次のように定義されます：

$$
    X ∖ Y = \{x \mid x ∈ X \text{ and } x ∉ Y \}
$$
