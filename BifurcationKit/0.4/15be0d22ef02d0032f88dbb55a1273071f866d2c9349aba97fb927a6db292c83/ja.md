```julia
continuation(
    coll,
    orbitguess,
    alg,
    _contParams,
    linear_algo;
    δ,
    eigsolver,
    record_from_solution,
    plot_solution,
    kwargs...
)

```

これは、直交コレクション法を使用して周期軌道を計算するための継続メソッドです。

# 引数

[`continuation`](@ref)と似ていますが、`prob`は[`PeriodicOrbitOCollProblem`](@ref)です。デフォルトでは、周期軌道の周期を出力します。

# キーワード引数

  * `eigsolver` フロケ特性指数の計算のための固有ソルバーを指定します。デフォルトは`FloquetQaD`です。
