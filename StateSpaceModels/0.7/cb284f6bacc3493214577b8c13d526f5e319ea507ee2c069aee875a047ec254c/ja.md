```
ExponentialSmoothing(
    y::Vector{Fl}; 
    trend::Bool = false,
    damped_trend::Bool = false,
    seasonal::Int = 0
) where Fl
```

線形指数平滑モデル。これらのモデルは文献ではETSとしても知られています。このモデルは線形ガウス状態空間モデルのカルマンフィルタを使用して推定されるため、可能なモデルは以下の加法誤差を持つETSです：

  * ETS(A, N, N)
  * ETS(A, A, N)
  * ETS(A, Ad, N)
  * ETS(A, N, A)
  * ETS(A, A, A)
  * ETS(A, Ad, A)

他のソフトウェアは拡張最小二乗法を使用しており、すべての可能なETSの組み合わせを持っています。カルマンフィルタアプローチは他の方法よりも遅いかもしれませんが、コンポーネントをフィルタリングする利点があります。

# 参考文献

  * Hyndman, Rob, Anne B. Koehler, J. Keith Ord, and Ralph D. Snyder. Forecasting with exponential smoothing: the state space approach. Springer Science & Business Media, 2008.
  * Hyndman, Robin John; Athanasopoulos, George.  Forecasting: Principles and Practice.  2nd ed. OTexts, 2018.
