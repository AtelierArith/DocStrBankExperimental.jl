```
NeuralDAE(model, constraints_model, tspan, args...; differential_vars = nothing,
    sensealg = TrackerAdjoint(), kwargs...)
```

ニューラル微分代数方程式（ニューラルDAE）を構築します。

引数:

  * `model`: 微分関数を定義する `Flux.Chain` または `Lux.AbstractLuxLayer` ニューラルネットワーク。サイズ `x` の入力を受け取り、微分変数に対してのみ `f(dx,x,t)` の残差を生成する必要があります。
  * `constraints_model`: 代数方程式に課す固定制約のための関数 `constraints_model(u,p,t)`。
  * `tspan`: 解決すべき時間範囲。
  * `alg`: ODEを解くために使用されるアルゴリズム。デフォルトは `nothing` で、すなわち DifferentialEquations.jl のデフォルトアルゴリズムです。
  * `sensealg`: 逆伝播で使用される微分アルゴリズムの選択。デフォルトは Tracker.jl を介した逆モード自動微分を使用します。
  * `kwargs`: ODEソルバーにスプラットされる追加の引数。詳細については [Common Solver Arguments](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/) ドキュメントを参照してください。
