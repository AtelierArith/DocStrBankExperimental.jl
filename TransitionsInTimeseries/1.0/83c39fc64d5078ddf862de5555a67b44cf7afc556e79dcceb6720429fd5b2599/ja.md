```
ar1_whitenoise(x::AbstractVector)
```

ホワイトノイズ仮定の下での最小二乗パラメータ推定の解析解を計算することによって、時系列 `x` のAR1回帰係数を返します：

$$
\theta = \sum_{i=2}^{n} x_i  x_{i-1} / \sum_{i=2}^{n} x_{i-1}^2
$$
