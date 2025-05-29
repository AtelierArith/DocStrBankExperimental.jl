```julia
newton(prob, orbitguess, options; lens, δ, kwargs...)

```

これは、(標準 / ポアンカレ) 射撃法を使用して周期軌道を計算するためのニュートン-クリロフソルバーです。線形ソルバーは `options` で適切に設定されている必要があります。

# 引数

[`newton`](@ref) と似ていますが、`prob` は [`ShootingProblem`](@ref) または [`PoincareShootingProblem`](@ref) のいずれかです。これらの2つの問題には調整するための特定のオプションがあり、詳細についてはそれらのリンクとチュートリアルを参照してください。

  * `prob` 射撃関数 G をエンコードするタイプ `<: AbstractShootingProblem` の問題。
  * `orbitguess` 周期軌道の推測。`orbitguess` の形状に関する情報は [`ShootingProblem`](@ref) および [`PoincareShootingProblem`](@ref) を参照してください。
  * `par` 関数に渡されるパラメータ
  * `options` 通常の [`newton`](@ref) メソッドと同じ。

# オプション引数

  * `jacobian` 線形アルゴリズムの選択を指定します。これは `[AutoDiffMF(), MatrixFree(), AutodiffDense(), AutoDiffDenseAnalytical(), FiniteDifferences(), FiniteDifferencesMF()]` のいずれかに属する必要があります。これは、ヤコビアン dG を反転する方法を選択するために使用されます。

      * `MatrixFree()` の場合、行列フリーのヤコビアンで、ヤコビアンは `prob` でユーザーによって指定されます。これは、線形システムを解くために反復ソルバー（例：GMRES）と一緒に使用されます。
      * `AutoDiffMF()` の場合、方向微分を使用して `x -> prob(x, p)` の（行列フリーの）導関数を計算するために自動微分（AD）を使用します。これは、線形システムを解くために反復ソルバー（例：GMRES）と一緒に使用されます。
      * `AutodiffDense()` の場合。`AutoDiffMF` と同様ですが、ヤコビアンは密な行列として形成されます。直接ソルバーまたは反復ソルバーを使用できます。
      * `FiniteDifferences()` の場合、`AutoDiffDense` と同様ですが、`δ = 1e-8` を引数として渡すことができるヤコビアン `x -> prob(x, p)` を計算するために有限差分を使用します。
      * `AutoDiffDenseAnalytical()` の場合。`AutoDiffDense` と同様ですが、ヤコビアンはADと解析式の混合を使用して形成されます。
      * `FiniteDifferencesMF()` の場合、`δ = 1e-8` を引数として渡すことができる `x -> prob(x, p)` の行列フリーのヤコビアンを計算するために有限差分を使用します。
