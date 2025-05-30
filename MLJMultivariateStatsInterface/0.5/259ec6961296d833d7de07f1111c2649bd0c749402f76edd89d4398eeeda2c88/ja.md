```
PCA
```

[MultivariateStats.jl](https://github.com/JuliaStats/MultivariateStats.jl)に基づいてpcaを構築するためのモデルタイプであり、MLJモデルインターフェースを実装しています。

MLJからは、次のようにしてタイプをインポートできます。

```
PCA = @load PCA pkg=MultivariateStats
```

`model = PCA()`を実行して、デフォルトのハイパーパラメータでインスタンスを構築します。ハイパーパラメータのデフォルトを上書きするには、`PCA(maxoutdim=...)`のようにキーワード引数を提供します。

主成分分析は、トレーニングデータで見られる初期の分散のほとんどを保持しながら、低次元空間への線形射影を学習します。

# トレーニングデータ

MLJまたはMLJBaseでは、次のようにしてデータにインスタンス`model`をバインドします。

```
mach = machine(model, X)
```

ここで：

  * `X`は、列がscitype `Continuous`である任意の入力特徴のテーブル（例：`DataFrame`）です。列のscitypesは`schema(X)`で確認できます。

`fit!(mach, rows=...)`を使用してマシンをトレーニングします。

# ハイパーパラメータ

  * `maxoutdim=0`：`variance_ratio`とともに、モデルによって選択される出力次元`outdim`を制御します。具体的には、`k`が最も重要な主成分の`k`を保持することでトレーニングデータの総分散の`variance_ratio`を占める最小の整数であるとします。すると、`outdim = min(outdim, maxoutdim)`となります。`maxoutdim=0`（デフォルト）の場合、実効的な`maxoutdim`は`min(n, indim - 1)`であり、ここで`n`は観測数、`indim`はトレーニングデータの特徴数です。
  * `variance_ratio::Float64=0.99`：変換後に保持される分散の比率
  * `method=:auto`：問題を解決するために使用するメソッド。選択肢は

      * `:svd`：行列のサポートベクタ分解。
      * `:cov`：共分散行列の分解。
      * `:auto`：行列の最初の次元が2番目の次元より小さい場合は`:cov`を使用し、それ以外の場合は`:svd`を使用します。
  * `mean=nothing`：`nothing`の場合、センタリングが計算され適用されます。`0`に設定された場合はセンタリングは行われません（データは事前にセンタリングされていると仮定されます）。ベクトルが渡された場合、そのベクトルを使用してセンタリングが行われます。

# 操作

  * `transform(mach, Xnew)`：入力`Xnew`の低次元射影を返します。`X`と同じscitypeを持つ必要があります。
  * `inverse_transform(mach, Xsmall)`：`transform`によって返されるような次元削減されたテーブル`Xsmall`に対して、元のトレーニングデータ`X`と同じ列数を持つテーブルを再構築し、`Xsmall`に変換します。数学的には、`inverse_transform`はPCA射影マップの右逆であり、その像はそのマップのカーネルに直交します。特に、`Xsmall = transform(mach, Xnew)`の場合、`inverse_transform(Xsmall)`は`Xnew`への近似に過ぎません。

# フィッティングパラメータ

`fitted_params(mach)`のフィールドは次のとおりです。

  * `projection`：サイズが`(indim, outdim)`の射影行列を返します。ここで、`indim`と`outdim`はそれぞれ入力と出力の特徴数です。

# レポート

`report(mach)`のフィールドは次のとおりです。

  * `indim`：トレーニングデータと変換される新しいデータの次元（列数）。
  * `outdim = min(n, indim, maxoutdim)`は出力次元です。ここで`n`は観測数です。
  * `tprincipalvar`：主成分の総分散。
  * `tresidualvar`：総残差分散。
  * `tvar`：総観測分散（主成分 + 残差分散）。
  * `mean`：変換されていないトレーニングデータの平均で、長さは`indim`です。
  * `principalvars`：主成分の分散。長さ`outdim`のAbstractVector
  * `loadings`：モデルのローディング、主成分を計算する際に使用される各変数の重み。サイズが(`indim`, `outdim`)の行列で、`indim`と`outdim`は上記のように定義されています。

# 例

```
using MLJ

PCA = @load PCA pkg=MultivariateStats

X, y = @load_iris # テーブルとベクトル

model = PCA(maxoutdim=2)
mach = machine(model, X) |> fit!

Xproj = transform(mach, X)
```

[`KernelPCA`](@ref)、[`ICA`](@ref)、[`FactorAnalysis`](@ref)、[`PPCA`](@ref)も参照してください。
