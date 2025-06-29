```
minkowski_difference(X::LazySet, Y::LazySet)
```

2つの集合のミンコフスキー差を計算します。

### 入力

  * `X` – 集合
  * `Y` – 集合

### 出力

ミンコフスキー差 $X ⊖ Y$ を表す集合。

### 注意事項

2つの集合 $X$ と $Y$ のミンコフスキー差は次のように定義されます。

$$
    X ⊖ Y = \{z \mid \{z\} ⊕ Y ⊆ X\}
$$

便利なエイリアス `pontryagin_difference` も利用可能です。

文献には命名規則に関するいくつかの不一致があります。このライブラリでは、*ミンコフスキー差* と *ポントリャーギン差* の両方が2つの集合の幾何学的差を指します。
