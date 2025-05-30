```
TerminateSteadyState(abstol = 1e-8, reltol = 1e-6, test = allDerivPass; min_t = nothing,
    wrap_test::Val = Val(true))
```

`TerminateSteadyState` は、問題の導関数が 0 に収束するまで、または `tspan[2]` に達するまでソルバーを実行することによって定常状態の問題を解決するために使用できます。これは、根を見つけるための代替アプローチです（[Steady State Solvers](https://docs.sciml.ai/DiffEqDocs/stable/solvers/steady_state_solve/) セクションを参照してください）。

## 引数

  * `abstol` と `reltol` は、それぞれ絶対許容誤差と相対許容誤差です。これらの許容誤差はスカラーまたは問題の状態と同じ長さの配列として指定できます。
  * `test` は、終了条件を評価する関数を表します。デフォルトの条件は、すべての導関数が `abstol` より小さくなるか、状態が `reltol` を掛けた値より小さくなることです。ユーザーは、異なる終了条件を実装するために他の関数を渡すことができます。そのような関数は、4 つの引数 `integrator`、`abstol`、`reltol`、および `min_t` を取る必要があります。
  * `wrap_test` は `Val(false)` に設定でき、その場合 `test` は `test(u, t, integrator)` という定義を持たなければなりません。それ以外の場合、`test` は `test(integrator, abstol, reltol, min_t)` という定義を持たなければなりません。

## キーワード引数

  * `min_t` は、定常状態の計算が終了する前に許可されるオプションの最小 `t` を指定します。
