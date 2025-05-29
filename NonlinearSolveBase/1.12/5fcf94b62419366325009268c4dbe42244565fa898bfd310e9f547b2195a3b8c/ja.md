```
construct_jacobian_cache(
    prob, alg, f, fu, u = prob.u0, p = prob.p;
    autodiff = nothing, vjp_autodiff = nothing, jvp_autodiff = nothing,
    linsolve = missing
)
```

`f`の`u`に関するヤコビアンのキャッシュを構築します。

### 引数

  * `prob`: [`NonlinearProblem`](@ref) または [`NonlinearLeastSquaresProblem`](@ref)。
  * `alg`: [`AbstractNonlinearSolveAlgorithm`](@ref)。[`concrete_jac`](@ref)のチェックに使用されます。
  * `f`: ヤコビアンを計算する関数。
  * `fu`: `f(u, p)` または `f(_, u, p)` の評価。結果キャッシュとヤコビアンのサイズを決定するために使用されます。
  * `u`: 現在の状態の値。
  * `p`: 現在のパラメータの値。

### キーワード引数

  * `autodiff`: ヤコビアンを計算するための自動微分または有限差分バックエンド。デフォルトでは、スパース性パラメータ、状態のタイプ、関数の特性などに基づいてバックエンドを選択します。
  * `vjp_autodiff`: ベクトル-ヤコビアン積を計算するための自動微分または有限差分バックエンド。
  * `jvp_autodiff`: ヤコビアン-ベクトル積を計算するための自動微分または有限差分バックエンド。
  * `linsolve`: 具体的なヤコビアンが必要か、可能であれば`JacobianOperator`を使用できるかを判断するために使用される線形ソルバーアルゴリズム。
