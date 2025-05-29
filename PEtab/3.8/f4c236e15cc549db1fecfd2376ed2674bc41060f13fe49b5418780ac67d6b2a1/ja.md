```
calibrate(prob::PEtabODEProblem, x0, alg; kwargs...)::PEtabOptimisationResult
```

出発点 `x0` から最適化アルゴリズム `alg` を使用して、`prob` の未知のモデルパラメータを推定し、結果を `PEtabOptimisationResult` として取得します。

`x0` は `Vector` または `ComponentArray` であり、個々のパラメータは `prob` が期待する順序でなければなりません。正しい順序のベクトルを取得するには、[`get_x`](@ref) を参照してください。

利用可能で推奨される最適化アルゴリズム (`alg`) のリストは、ドキュメントに記載されています。簡単に言うと、サポートされているアルゴリズムは以下の通りです：

  * [Optim.jl](https://julianlsolvers.github.io/Optim.jl/stable/): `LBFGS()`, `BFGS()`, または `IPNewton()` メソッド。
  * [Ipopt.jl](https://coin-or.github.io/Ipopt/): `IpoptOptimizer()` 内点ニュートン法。
  * [Fides.py](https://github.com/fides-dev/fides): `Fides()` ニュートン信頼領域法。

パラメータ推定結果を視覚化するためのさまざまな方法は、ドキュメントに記載されています。

また、[`PEtabOptimisationResult`](@ref)、[`Fides`](@ref)、および [`IpoptOptimizer`](@ref) も参照してください。

## キーワード引数

  * `save_trace::Bool = false`: 目的関数とパラメータベクトルの最適化トレースを保存するかどうか。いくつかのアルゴリズムにのみ適用可能です。詳細はドキュメントを参照してください。
  * `options = DEFAULT_OPTIONS`: `alg` のための設定可能なオプション。タイプと利用可能なオプションは、`alg` が属するパッケージによって異なります。たとえば、`alg = IPNewton()` が Optim.jl からの場合、`options` は `Optim.Options()` 構造体として提供されるべきです。設定可能なオプションのリストは、ドキュメントに記載されています。
