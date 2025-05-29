```
FiniteDifference([N; pre])
```

有限差分に基づくアルゴリズム。

# 引数

  * `N=500`: 空間グリッド内の点の数。

# キーワード引数

  * `pre=nothing`: 互換性のある `AbstractFiniteProblem` の解法を高速化するために `BoltzmannODE()` に設定します。

参照: [`solve`](@ref), [`AbstractFiniteProblem`](@ref), [`BoltzmannODE`](@ref)
