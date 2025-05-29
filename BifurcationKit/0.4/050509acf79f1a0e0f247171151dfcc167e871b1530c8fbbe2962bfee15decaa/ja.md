```julia
generate_ci_problem(
    pb,
    bifprob,
    sol,
    tspan;
    optimal_period,
    ktrap...
)

```

解の周期軌道問題を生成します。

## 引数

  * `pb` 基本情報を提供する `PeriodicOrbitTrapProblem`、例えば時間スライスの数 `M`
  * `bifprob` ベクトル場を提供するための分岐問題
  * `sol` 基本的には `ODEProblem`
  * `tspan = (0,1.)` 周期軌道の時間範囲（周期）の推定

## 出力

  * `PeriodicOrbitTrapProblem` と初期推定を返します。
