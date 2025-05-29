```
cartesian_product(X::LazySet, Y::LazySet)
```

2つの集合の直積を計算します。

### 入力

  * `X` – 集合
  * `Y` – 集合

### 出力

直積 $X × Y$ を表す集合。

### 注意事項

2つの集合 $X$ と $Y$ の直積は次のように定義されます。

$$
    X × Y = \{[x, y] \mid x ∈ X, y ∈ Y\}.
$$
