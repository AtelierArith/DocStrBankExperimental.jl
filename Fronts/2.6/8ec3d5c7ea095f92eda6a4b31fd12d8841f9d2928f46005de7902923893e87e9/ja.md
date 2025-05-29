```
InverseProblem(o, u[, weights; i, b, ob])
```

実験データを用いた逆関数およびパラメータ推定の問題タイプ。

# 引数

  * `o::AbstractVector`: ボルツマン変数の値。[`o`](@ref)を参照してください。
  * `u::AbstractVector`: `o`の各点での観測された解の値。
  * `weights`: データのオプションの重み。

# キーワード引数

  * `i`: 初期値（既知の場合）。
  * `b`: 境界値（既知の場合）。
  * `ob=0`: 境界での`o`の値。

# 参照

[`diffusivity`](@ref), [`sorptivity`](@ref), `Fronts.ParamEstim`
