```
KalmanSettings(Y::Union{FloatMatrix, JMatrix{Float64}}, B::FloatMatrix, R::Union{UniformScaling{Float64}, SymMatrix}, C::FloatMatrix, D::FloatMatrix, Q::SymMatrix; kwargs...)
```

`KalmanSettings` コンストラクタ。

# 引数

  * `Y`: 観測された測定値 (`nxT`)
  * `B`: 測定方程式の係数
  * `R`: 測定方程式の誤差項の共分散行列
  * `C`: 遷移方程式の係数
  * `D`: 誤差項に関連する遷移方程式の係数
  * `Q`: 遷移方程式の誤差項の共分散行列

# キーワード引数

  * `compute_loglik`: ブール値（カルマンフィルタでの対数尤度を計算する場合は `true` - デフォルト: `true`）
  * `store_history`: ブール値（フィルタとスムーザーの履歴を保存する場合は `true` - デフォルト: `true`）

# 注意事項

この特定のコンストラクタは `X0` をゼロのベクトルに設定し、`solve_discrete_lyapunov(C, Q)` を介して `P0` を計算します。 ```
