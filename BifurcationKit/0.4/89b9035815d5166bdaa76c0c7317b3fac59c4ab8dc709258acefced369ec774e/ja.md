```julia
generate_ci_problem(
    pb,
    bifprob,
    sol_ode,
    period;
    cache_In,
    optimal_period
)

```

解法から周期軌道問題を生成します。

## 引数

  * `pb` 基本情報を提供する `PeriodicOrbitOCollProblem`、例えば時間スライスの数 `M`
  * `bifprob` ベクトル場を提供するための分岐問題
  * `sol` 基本的には `ODEProblem` または関数 `t -> sol(t)`
  * `period` 周期軌道の周期の推定値

## 出力

  * `PeriodicOrbitOCollProblem` と初期推定値を返します。
