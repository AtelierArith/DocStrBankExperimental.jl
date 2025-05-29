```
auto_ets(y::Vector{Fl}; seasonal::Int = 0) where Fl
```

最適な AIC に基づいて最適な [`ExponentialSmoothing`](@ref) モデルを自動的にフィットします。モデルの間で:

  * ETS(A, N, N)
  * ETS(A, A, N)
  * ETS(A, Ad, N)

ユーザーが時系列の季節性を提供した場合、モデルの間で検索します。

  * ETS(A, N, A)
  * ETS(A, A, A)
  * ETS(A, Ad, A)

# 参考文献

  * Hyndman, Robin John; Athanasopoulos, George.

Forecasting: Principles and Practice.   2nd ed. OTexts, 2018. ```
