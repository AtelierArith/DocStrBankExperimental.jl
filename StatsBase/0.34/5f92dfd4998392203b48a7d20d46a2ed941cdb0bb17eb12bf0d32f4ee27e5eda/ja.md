```
pacf!(r, X, lags; method=:regression)
```

行列 `X` の偏自己相関関数 (PACF) を `lags` で計算し、結果を `r` に格納します。`method` は推定方法を指定します。認識される値は `:regression` で、これは連続回帰モデルを介して偏自己相関を計算し、`:yulewalker` で、これは Yule-Walker 方程式を使用して偏自己相関を計算します。

`r` はサイズ `(length(lags), size(x, 2))` の行列でなければなりません。
