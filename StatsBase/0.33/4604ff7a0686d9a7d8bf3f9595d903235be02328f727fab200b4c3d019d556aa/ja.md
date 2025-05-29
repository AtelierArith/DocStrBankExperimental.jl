```
pacf(X, lags; method=:regression)
```

実数ベクトルまたは行列 `X` の部分自己相関関数 (PACF) を `lags` で計算します。`method` は推定方法を指定します。認識される値は `:regression` で、これは連続回帰モデルを通じて部分自己相関を計算し、`:yulewalker` で、これは Yule-Walker 方程式を使用して部分自己相関を計算します。

もし `x` がベクトルであれば、`lags` と同じ長さのベクトルを返します。もし `x` が行列であれば、サイズが `(length(lags), size(x, 2))` の行列を返し、結果の各列は `x` の列に対応します。
