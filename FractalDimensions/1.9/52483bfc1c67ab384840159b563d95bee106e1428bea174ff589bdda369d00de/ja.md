```
kaplanyorke_dim(λs::AbstractVector)
```

与えられたリャプノフ指数 `λs` からカプラン-ヨーク次元、すなわちリャプノフ次元 [Kaplan1979](@cite) を計算します。

## 説明

カプラン-ヨーク次元は、単に `cumsum(λs)` がゼロになる点（補間された）です：

$$
 D_{KY} = k + \frac{\sum_{i=1}^k \lambda_i}{|\lambda_{k+1}|},\quad k = \max_j \left[ \sum_{i=1}^j \lambda_i > 0 \right].
$$

指数の合計が決して負にならない場合、関数は入力ベクトルの長さを返します。

ChaosTools.jl の `lyapunovspectrum` と組み合わせて使用するのに便利です。
