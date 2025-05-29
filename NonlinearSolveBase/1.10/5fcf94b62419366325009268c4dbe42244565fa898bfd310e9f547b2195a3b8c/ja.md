```
construct_jacobian_cache(
    prob, alg, f, fu, u = prob.u0, p = prob.p;
    autodiff = nothing, vjp_autodiff = nothing, jvp_autodiff = nothing,
    linsolve = missing
)
```

`f` に関する `u` のヤコビ行列のキャッシュを構築します。

### 引数

  * `prob`: [`NonlinearProblem`](@ref) または [`NonlinearLeastSquaresProblem`](@ref)。
  * `alg`: [`AbstractNonlinearSolveAlgorithm`](@ref)。[`concrete_jac`](@ref) のチェックに使用されます。
  * `f`: ヤコビ行列を計算する関数。
  * `fu`: `f(u, p)` または `f(_, u, p)` の評価。結果キャッシュとヤコビ行列のサイズを決定するために使用されます。
  * `u`: 現在の状態の値。
  * `p`: 現在のパラメータの値。

### キーワード引数

  * `autodiff`: ヤコビ行列を計算するための自動微分または有限差分バックエンド。デフォルトでは、スパース性パラメータ、状態のタイプ、関数の特性などに基づいてバックエンドを選択します。
  * `vjp_autodiff`: ベクトル-ヤコビ行列積を計算するための自動微分または有限差分バックエンド。
  * `jvp_autodiff`: ヤコビ行列-ベクトル積を計算するための自動微分または有限差分バックエンド。
  * `linsolve`: 具体的なヤコビ行列が必要か、可能であれば `JacobianOperator` を使用できるかを判断するために使用される線形ソルバーアルゴリズム。
