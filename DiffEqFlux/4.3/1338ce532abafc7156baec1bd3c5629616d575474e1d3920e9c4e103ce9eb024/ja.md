```
NeuralODE(model, tspan, alg = nothing, args...; kwargs...)
```

連続時間再帰神経ネットワーク、または神経常微分方程式（neural ODE）を構築し、随伴を介して高速な勾配計算を行います[1]。高レベルでは、これは前方微分方程式を解くことに対応し、損失の導関数を時間的に逆に伝播させる第二の微分方程式を使用します。

引数:

  * `model`: ̇xを定義する`Flux.Chain`または`Lux.AbstractLuxLayer`神経ネットワーク。
  * `tspan`: 解決される時間範囲。
  * `alg`: ODEを解くために使用されるアルゴリズム。デフォルトは`nothing`、すなわちDifferentialEquations.jlのデフォルトアルゴリズムです。
  * `sensealg`: 逆伝播で使用される微分アルゴリズムの選択。デフォルトは随伴法です。詳細については、[ローカル感度分析](https://docs.sciml.ai/SciMLSensitivity/stable/)のドキュメントを参照してください。
  * `kwargs`: ODEソルバーにスプラットされた追加の引数。詳細については、[共通ソルバー引数](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/)のドキュメントを参照してください。

参考文献:

[1] Pontryagin, Lev Semenovich. Mathematical theory of optimal processes. CRC press, 1987.
