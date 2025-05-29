```
FFJORD(model, tspan, input_dims, args...; ad = nothing, basedist = nothing, kwargs...)
```

連続時間再帰神経ネットワーク、または神経常微分方程式（neural ODE）を構築し、隣接を介した高速勾配計算を行い[1]、連続正規化フロー（CNF）[2]に基づく密度推定に特化し、動的ジャコビアンのトレースの計算に対して確率的アプローチ[2]を使用します。高レベルでは、これは以下のステップに対応します：

1. 興味のある変数 x(t) を、既知の密度 p_z を持つ基準変数 z(t) の関数 f(z, θ, t) としてパラメータ化します。
2. 変数の変換公式を使用して、密度 p*x を密度 p*z と f のジャコビアンのトレースの関数として予測します。
3. 密度 p_x の損失関数を最小化するようにパラメータ θ を選択します（通常はデータの負の尤度）。

これらのステップの後、NNモデルと学習した θ を使用して、新しい x の値に対する密度 p_x を予測できます。

引数：

  * `model`: モデルの動的を定義する `Flux.Chain` または `Lux.AbstractLuxLayer` 神経ネットワーク。
  * `basedist`: 基準変数の分布。デフォルトでは単位正規分布に設定されています。
  * `input_dims`: モデルの入力次元。
  * `tspan`: 解決すべき時間範囲。
  * `args`: ODEソルバーにスプラットされた追加の引数。詳細については、[Common Solver Arguments](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/) ドキュメントを参照してください。
  * `ad`: 内部ジャコビアンのトレースに使用する自動微分法。完全なジャコビアンを計算する必要がある場合は `AutoForwardDiff()` にデフォルト設定されます。すなわち、`monte_carlo = false` の場合です。それ以外の場合は `AutoZygote()` を使用します。
  * `kwargs`: ODEソルバーにスプラットされた追加の引数。詳細については、[Common Solver Arguments](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/) ドキュメントを参照してください。

参考文献：

[1] Pontryagin, Lev Semenovich. Mathematical theory of optimal processes. CRC press, 1987.

[2] Chen, Ricky TQ, Yulia Rubanova, Jesse Bettencourt, and David Duvenaud. "Neural ordinary differential equations." In Proceedings of the 32nd International Conference on Neural Information Processing Systems, pp. 6572-6583. 2018.

[3] Grathwohl, Will, Ricky TQ Chen, Jesse Bettencourt, Ilya Sutskever, and David Duvenaud. "Ffjord: Free-form continuous dynamics for scalable reversible generative models." arXiv preprint arXiv:1810.01367 (2018).
