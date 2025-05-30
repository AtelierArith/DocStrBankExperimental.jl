```
FactorAnalysis
```

[MultivariateStats.jl](https://github.com/JuliaStats/MultivariateStats.jl)に基づいて因子分析モデルを構築するためのモデルタイプであり、MLJモデルインターフェースを実装しています。

MLJからは、次のようにしてタイプをインポートできます。

```
FactorAnalysis = @load FactorAnalysis pkg=MultivariateStats
```

`model = FactorAnalysis()`を実行して、デフォルトのハイパーパラメータでインスタンスを構築します。ハイパーパラメータのデフォルトをオーバーライドするには、`FactorAnalysis(method=...)`のようにキーワード引数を提供します。

因子分析は、確率的PCAに密接に関連する線形-ガウス潜在変数モデルです。確率的PCAモデルとは対照的に、潜在変数が与えられたときの観測変数の条件付き分布の共分散は、等方的ではなく対角的です。

# トレーニングデータ

MLJまたはMLJBaseでは、次のようにしてデータにインスタンス`model`をバインドします。

```
mach = machine(model, X)
```

ここで：

  * `X`は、列がscitype `Continuous`である任意の入力特徴のテーブル（例：`DataFrame`）です。列のscitypesは`schema(X)`で確認できます。

`fit!(mach, rows=...)`を使用してマシンをトレーニングします。

# ハイパーパラメータ

  * `method::Symbol=:cm`: 問題を解決するために使用するメソッドで、`:ml`、`:em`、`:bayes`のいずれかです。
  * `maxoutdim=0`: 出力の次元（列数）`outdim`を制御します。具体的には、`outdim = min(n, indim, maxoutdim)`で、ここで`n`は観測数、`indim`は入力次元です。
  * `maxiter::Int=1000`: 最大反復回数。
  * `tol::Real=1e-6`: 収束許容範囲。
  * `eta::Real=tol`: 分散の下限。
  * `mean::Union{Nothing, Real, Vector{Float64}}=nothing`: `nothing`の場合、センタリングが計算され適用されます。`0`に設定するとセンタリングは適用されません（データは事前にセンタリングされていると仮定されます）。ベクトルの場合、そのベクトルでセンタリングが行われます。

# 操作

  * `transform(mach, Xnew)`: 入力`Xnew`の低次元投影を返します。`Xnew`は上記の`X`と同じscitypeである必要があります。
  * `inverse_transform(mach, Xsmall)`: `transform`によって返されたような次元削減されたテーブル`Xsmall`に対して、元のトレーニングデータ`X`と同じ列数を持つテーブルを再構築し、`Xsmall`に変換します。数学的には、`inverse_transform`はPCA投影マップの右逆であり、その像はそのマップのカーネルに直交します。特に、`Xsmall = transform(mach, Xnew)`の場合、`inverse_transform(Xsmall)`は`Xnew`への近似に過ぎません。

# フィッティングされたパラメータ

`fitted_params(mach)`のフィールドは次のとおりです。

  * `projection`: 投影行列を返します。サイズは`(indim, outdim)`で、`indim`と`outdim`はそれぞれ入力と出力の特徴の数です。投影行列の各列は因子に対応します。

# レポート

`report(mach)`のフィールドは次のとおりです。

  * `indim`: トレーニングデータと変換される新しいデータの次元（列数）。
  * `outdim`: 変換されたデータの次元（因子の数）。
  * `variance`: 因子の分散。
  * `covariance_matrix`: 推定された共分散行列。
  * `mean`: 元のトレーニングデータの平均で、長さは`indim`です。
  * `loadings`: 因子負荷。サイズは(`indim`, `outdim`)の行列で、`indim`と`outdim`は上記のように定義されています。

# 例

```
using MLJ

FactorAnalysis = @load FactorAnalysis pkg=MultivariateStats

X, y = @load_iris # テーブルとベクトル

model = FactorAnalysis(maxoutdim=2)
mach = machine(model, X) |> fit!

Xproj = transform(mach, X)
```

[`KernelPCA`](@ref)、[`ICA`](@ref)、[`PPCA`](@ref)、[`PCA`](@ref)も参照してください。
