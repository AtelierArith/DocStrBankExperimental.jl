```
NeuralDSDE(drift, diffusion, tspan, alg = nothing, args...; sensealg = TrackerAdjoint(),
    kwargs...)
```

対角ノイズを持つニューラル確率微分方程式（ニューラル SDE）を構築します。

引数:

  * `drift`: ドリフト関数を定義する `Flux.Chain` または `Lux.AbstractLuxLayer` ニューラルネットワーク。
  * `diffusion`: 拡散関数を定義する `Flux.Chain` または `Lux.AbstractLuxLayer` ニューラルネットワーク。入力と同じサイズのベクトルを出力する必要があります。
  * `tspan`: 解決する時間範囲。
  * `alg`: ODEを解くために使用されるアルゴリズム。デフォルトは `nothing` で、すなわち DifferentialEquations.jl のデフォルトアルゴリズムです。
  * `sensealg`: バックプロパゲーションで使用される微分アルゴリズムの選択。
  * `kwargs`: ODEソルバーにスプラットされる追加の引数。詳細については、[Common Solver Arguments](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/) ドキュメントを参照してください。
