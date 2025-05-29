```
NeuralCDDE(model, tspan, hist, lags, alg = nothing, args...;
    sensealg = TrackerAdjoint(), kwargs...)
```

定常遅延を持つニューラル遅延微分方程式（ニューラル DDE）を構築します。

引数:

  * `model`: 微分関数を定義する `Flux.Chain` または `Lux.AbstractLuxLayer` ニューラルネットワーク。サイズ `[x; x(t - lag_1); ...; x(t - lag_n)]` の入力を受け取り、`x` の形状の出力を生成する必要があります。
  * `tspan`: 解決すべき時間範囲。
  * `hist`: 統合の開始前の値に対する履歴関数 `h(u, p, t)` を定義します。`u` は `u` のサイズに一致する値を返すために使用されることになっています。
  * `lags`: ニューラルネットワークで利用されるべき遅延値を定義します。
  * `alg`: ODEを解くために使用されるアルゴリズム。デフォルトは `nothing`、すなわち DifferentialEquations.jl のデフォルトアルゴリズムです。
  * `sensealg`: 逆伝播で使用される微分アルゴリズムの選択。デフォルトは Tracker.jl を介した逆モード自動微分を使用します。
  * `kwargs`: ODEソルバーにスプラットされる追加の引数。詳細については [Common Solver Arguments](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/) ドキュメントを参照してください。
