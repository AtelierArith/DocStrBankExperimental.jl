この関数は回帰問題を解決するために使用されます。パラメータのベクトルを返します。

```
physics_informed_regression(sys::AbstractTimeDependentSystem, u::Vector, du::Vector)
physics_informed_regression(sys::AbstractTimeDependentSystem, u::Vector, du::Vector, A::Matrix, b::Vector)
kwargs: lambda = 0.0 (正則化パラメータ)
```

# 引数

  * `sys`: パラメータを解決するための方程式のシステム (ODESystem または DAESystem)
  * `u`: 状態のベクトル
  * `du`: 微分のベクトル
  * `A`: 方程式 A*x = b における記号的行列 A
  * `b`: 方程式 A*x = b における記号的ベクトル b

# 戻り値

  * `paramsest`: 推定されたパラメータのベクトル
