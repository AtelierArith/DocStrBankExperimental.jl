```julia
newton(prob, orbitguess, defOp, options; lens, kwargs...)

```

これは、（標準 / ポアンカレ）シューティング法を使用して周期軌道を計算するための縮退ニュートン-クリロフソルバーです。

# 引数

[`newton`](@ref)と似ていますが、`prob`は[`ShootingProblem`](@ref)または[`PoincareShootingProblem`](@ref)のいずれかです。

# オプション引数

  * `jacobian` 線形アルゴリズムの選択を指定します。これは`[AutoDiffMF(), MatrixFree(), AutodiffDense(), AutoDiffDenseAnalytical(), FiniteDifferences(), FiniteDifferencesMF()]`のいずれかに属する必要があります。これは、ヤコビアンdGを反転する方法を選択するために使用されます。

      * `MatrixFree()`の場合、行列フリーのヤコビアンで、ヤコビアンはユーザーによって`prob`で指定されます。これは、線形システムを解くために反復ソルバー（例：GMRES）と一緒に使用されます。
      * `AutoDiffMF()`の場合、自動微分（AD）を使用して`x -> prob(x, p)`の（行列フリー）導関数を方向微分を使用して計算します。これは、線形システムを解くために反復ソルバー（例：GMRES）と一緒に使用されます。
      * `AutodiffDense()`の場合。`AutoDiffMF`と同様ですが、ヤコビアンは密な行列として形成されます。直接ソルバーまたは反復ソルバーを使用できます。
      * `FiniteDifferences()`の場合、`AutoDiffDense`と同様ですが、有限差分を使用して`x -> prob(x, p)`のヤコビアンを計算します。`δ = 1e-8`を引数として渡すことができます。
      * `AutoDiffDenseAnalytical()`の場合。`AutoDiffDense`と同様ですが、ヤコビアンはADと解析式の混合を使用して形成されます。
      * `FiniteDifferencesMF()`の場合、有限差分を使用して`x -> prob(x, p)`の行列フリーのヤコビアンを計算します。`δ = 1e-8`を引数として渡すことができます。

# 出力:

  * solution::NonLinearSolution、詳細は[`NonLinearSolution`](@ref)を参照してください。

```
