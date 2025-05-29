```
ShepardInterpolator(X, y, a=3)
```

n次元の点の集合に対して `ShepardInterpolator` を構築します。座標 `X` と値 `y` を持ちます。`X` は p × N の配列で、p は点の数、N は次元の数です。`y` は長さ p のベクトルでなければなりません。`a` の値は距離重み付け関数 $r^{-a}$ を定義します。
