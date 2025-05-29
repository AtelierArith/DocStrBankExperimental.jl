```
QuasiNewtonAlgorithm(;
    linesearch = missing, trustregion = missing, descent, update_rule, reinit_rule,
    initialization, max_resets::Int = typemax(Int), name::Symbol = :unknown,
    max_shrink_times::Int = typemax(Int), concrete_jac = Val(false)
)
```

ヤコビアンの反復近似を使用した非線形解法アルゴリズム。最も一般的な例には[`Broyden`](@ref)の方法が含まれます。

### キーワード引数

  * `trustregion`: トラスト領域法を使用したグローバリゼーション。これは[`NonlinearSolveBase.AbstractTrustRegionMethod`](@ref)インターフェースに従う必要があります。
  * `descent`: ステップを計算するために使用する降下法。この方法は[`NonlinearSolveBase.AbstractDescentDirection`](@ref)インターフェースに従う必要があります。
  * `max_shrink_times`: アルゴリズムが終了する前にトラスト領域半径を縮小できる最大回数。
  * `update_rule`: ヤコビアンを更新するために使用する更新ルール。このルールは[`NonlinearSolveBase.AbstractApproximateJacobianUpdateRule`](@ref)インターフェースに従う必要があります。
  * `reinit_rule`: ヤコビアンを再初期化するために使用する再初期化ルール。このルールは[`NonlinearSolveBase.AbstractResetCondition`](@ref)インターフェースに従う必要があります。
  * `initialization`: ヤコビアンを初期化するために使用する初期化方法。この方法は[`NonlinearSolveBase.AbstractJacobianInitialization`](@ref)インターフェースに従う必要があります。
