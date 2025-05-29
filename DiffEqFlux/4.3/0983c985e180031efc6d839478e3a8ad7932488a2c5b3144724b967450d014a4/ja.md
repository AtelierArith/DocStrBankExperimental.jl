```
NeuralODEMM(model, constraints_model, tspan, mass_matrix, alg = nothing, args...;
    sensealg = InterpolatingAdjoint(autojacvec = ZygoteVJP()), kwargs...)
```

物理的制約のある連続時間再帰ニューラルネットワーク、別名ニューラル微分代数方程式（neural DAE）を構築します。質量行列と、随伴を介した高速勾配計算を使用します[1]。質量行列の定式化は次のとおりです：

$$
Mu' = f(u,p,t)
$$

ここで、`M`は半明示的であり、すなわち制約方程式に対応する行にゼロを持つ特異なものです。

引数：

  * `model`: `f(u,p,t)`を定義する`Flux.Chain`または`Lux.AbstractLuxLayer`ニューラルネットワーク。
  * `constraints_model`: 代数方程式に課す固定制約のための関数`constraints_model(u,p,t)`。
  * `tspan`: 解決すべき時間範囲。
  * `mass_matrix`: DAEに関連する質量行列。
  * `alg`: ODEを解くために使用されるアルゴリズム。デフォルトは`nothing`、すなわちDifferentialEquations.jlのデフォルトアルゴリズムです。このメソッドは、特異質量行列に対応した暗黙のODEソルバーを必要とします。詳細については、[DAE solvers](https://docs.sciml.ai/DiffEqDocs/stable/solvers/dae_solve/)のドキュメントを参照してください。
  * `sensealg`: 逆伝播で使用される微分アルゴリズムの選択。デフォルトは随伴法です。詳細については、[Local Sensitivity Analysis](https://docs.sciml.ai/SciMLSensitivity/stable/)のドキュメントを参照してください。
  * `kwargs`: ODEソルバーにスプラットされた追加の引数。詳細については、[Common Solver Arguments](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/)のドキュメントを参照してください。
