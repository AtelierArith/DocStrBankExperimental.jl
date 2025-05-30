```
PPCA
```

確率的PCAモデルを構築するためのモデルタイプで、[MultivariateStats.jl](https://github.com/JuliaStats/MultivariateStats.jl)に基づき、MLJモデルインターフェースを実装しています。

MLJからは、次のようにしてタイプをインポートできます。

```
PPCA = @load PPCA pkg=MultivariateStats
```

`model = PPCA()`を実行して、デフォルトのハイパーパラメータを持つインスタンスを構築します。ハイパーパラメータのデフォルトを上書きするには、`PPCA(maxoutdim=...)`のようにキーワード引数を提供します。

確率的主成分分析は、自由パラメータの数を制限しながらも、データセット内の支配的な相関をモデルが捉えることを可能にする、ガウス分布の制約された形を表す次元削減アルゴリズムです。これは、確率的潜在変数モデルの最大尤度解として表現されます。詳細については、Bishop (2006): C. M. Pattern Recognition and Machine Learningを参照してください。

# トレーニングデータ

MLJまたはMLJBaseでは、次のようにしてインスタンス`model`をデータにバインドします。

```
mach = machine(model, X)
```

ここで：

  * `X`は、列がscitype `Continuous`である任意の入力特徴のテーブル（例：`DataFrame`）です。列のscitypesは`schema(X)`で確認できます。

`fit!(mach, rows=...)`を使用してマシンをトレーニングします。

# ハイパーパラメータ

  * `maxoutdim=0`: 出力の次元（列の数）`outdim`を制御します。具体的には、`outdim = min(n, indim, maxoutdim)`であり、ここで`n`は観測の数、`indim`は入力次元です。
  * `method::Symbol=:ml`: 問題を解決するために使用するメソッドで、`:ml`、`:em`、`:bayes`のいずれかです。
  * `maxiter::Int=1000`: 最大反復回数です。
  * `tol::Real=1e-6`: 収束許容値です。
  * `mean::Union{Nothing, Real, Vector{Float64}}=nothing`: `nothing`の場合、センタリングが計算され適用されます。`0`に設定された場合、センタリングは適用されません（データは事前にセンタリングされていると仮定されます）。ベクトルが指定された場合、そのベクトルでセンタリングが行われます。

# 操作

  * `transform(mach, Xnew)`: 入力`Xnew`の低次元投影を返します。`X`と同じscitypeを持つ必要があります。
  * `inverse_transform(mach, Xsmall)`: `transform`によって返された次元削減されたテーブル`Xsmall`に対して、元のトレーニングデータ`X`と同じ列数を持つテーブルを再構築します。数学的には、`inverse_transform`はPCA投影マップの右逆であり、その像はそのマップのカーネルに直交します。特に、`Xsmall = transform(mach, Xnew)`の場合、`inverse_transform(Xsmall)`は`Xnew`への近似に過ぎません。

# フィッティングされたパラメータ

`fitted_params(mach)`のフィールドは次のとおりです。

  * `projection`: 投影行列を返します。サイズは`(indim, outdim)`であり、`indim`と`outdim`はそれぞれ入力と出力の特徴の数です。投影行列の各列は主成分に対応します。

# レポート

`report(mach)`のフィールドは次のとおりです。

  * `indim`: トレーニングデータと変換される新しいデータの次元（列の数）。
  * `outdim`: 変換されたデータの次元。
  * `tvat`: コンポーネントの分散。
  * `loadings`: モデルのローディング行列。サイズは(`indim`, `outdim`)であり、`indim`と`outdim`は上記のように定義されています。

# 例

```
using MLJ

PPCA = @load PPCA pkg=MultivariateStats

X, y = @load_iris # テーブルとベクトル

model = PPCA(maxoutdim=2)
mach = machine(model, X) |> fit!

Xproj = transform(mach, X)
```

[`KernelPCA`](@ref)、[`ICA`](@ref)、[`FactorAnalysis`](@ref)、[`PCA`](@ref)も参照してください。
