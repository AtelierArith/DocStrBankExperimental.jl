```
prob_Gaussian_grid(par, reporters_per_state, Nstate, Ngrid, f::Function=kronecker_delta)
```

与えられたパラメータと状態ごとのレポータに基づいて、正規分布の3D配列を生成します。

# 引数

  * `par`: ガウス分布のパラメータ。
  * `reporters_per_state`: 状態ごとのレポータの数。
  * `Nstate`: 状態の数。
  * `Ngrid`: 位置の数。
  * `f::Function`: クロネッカーのデルタに使用する関数（デフォルトは `kronecker_delta`）。

# 戻り値

  * `Array{Distribution{Univariate,Continuous}}`: 正規分布の3D配列。
