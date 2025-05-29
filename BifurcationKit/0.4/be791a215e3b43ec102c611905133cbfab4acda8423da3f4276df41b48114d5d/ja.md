```julia
continuation(
    probPO,
    orbitguess,
    alg,
    contParams,
    linear_algo;
    δ,
    eigsolver,
    record_from_solution,
    plot_solution,
    kwargs...
)

```

これは、（標準 / ポアンカレ）シューティング法を使用して周期軌道を計算するための継続メソッドです。

# 引数

[`continuation`](@ref) と似ていますが、`probPO` は [`ShootingProblem`](@ref) または [`PoincareShootingProblem`](@ref) のいずれかです。デフォルトでは、周期軌道の周期を出力します。

# オプション引数

  * `eigsolver` フロケ特性根の計算のための固有ソルバーを指定します。デフォルトは `FloquetQaD` です。
  * `jacobian` 線形アルゴリズムの選択を指定します。これは `[AutoDiffMF(), MatrixFree(), AutodiffDense(), AutoDiffDenseAnalytical(), FiniteDifferences(), FiniteDifferencesMF()]` のいずれかに属する必要があります。これは、ヤコビアン dG を反転する方法を選択するために使用されます。

      * `MatrixFree()` の場合、行列フリーのヤコビアンで、ヤコビアンはユーザーによって `prob` に指定されます。これは、線形システムを解くために反復ソルバー（例：GMRES）と一緒に使用されます。
      * `AutoDiffMF()` の場合、方向微分を使用して `x -> prob(x, p)` の（行列フリー）導関数を計算するために自動微分（AD）を使用します。これは、線形システムを解くために反復ソルバー（例：GMRES）と一緒に使用されます。
      * `AutodiffDense()` の場合。`AutoDiffMF` と同様ですが、ヤコビアンは密な行列として形成されます。直接ソルバーまたは反復ソルバーを使用できます。
      * `FiniteDifferences()` の場合、`AutoDiffDense` と同様ですが、`δ = 1e-8` を引数として渡すことができる有限差分を使用して `x -> prob(x, p)` のヤコビアンを計算します。
      * `AutoDiffDenseAnalytical()` の場合。`AutoDiffDense` と同様ですが、ヤコビアンはADと解析式の混合を使用して形成されます。
      * `FiniteDifferencesMF()` の場合、`δ = 1e-8` を引数として渡すことができる有限差分を使用して `x -> prob(x, p)` の行列フリーのヤコビアンを計算します。
