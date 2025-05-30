```
BayesianSubspaceLDA
```

ベイズサブスペースLDAモデルを構築するためのモデルタイプで、[MultivariateStats.jl](https://github.com/JuliaStats/MultivariateStats.jl)に基づいており、MLJモデルインターフェースを実装しています。

MLJからは、次のようにしてタイプをインポートできます。

```
BayesianSubspaceLDA = @load BayesianSubspaceLDA pkg=MultivariateStats
```

`model = BayesianSubspaceLDA()`を実行して、デフォルトのハイパーパラメータを持つインスタンスを構築します。ハイパーパラメータのデフォルトを上書きするには、`BayesianSubspaceLDA(normalize=...)`のようにキーワード引数を提供します。

ベイズ多クラスサブスペース線形判別分析アルゴリズムは、[`SubspaceLDA`](@ref)で説明されているように、射影行列を学習します。事後クラス確率分布は、[`BayesianLDA`](@ref)のように導出されます。

# トレーニングデータ

MLJまたはMLJBaseでは、次のようにしてインスタンス`model`をデータにバインドします。

```
mach = machine(model, X, y)
```

ここで：

  * `X`は、列がスカイタイプ`Continuous`の入力特徴の任意のテーブル（例：`DataFrame`）です。列のスカイタイプは`schema(X)`で確認できます。
  * `y`は、要素のスカイタイプが`OrderedFactor`または`Multiclass`の任意の`AbstractVector`です。スカイタイプは`scitype(y)`で確認できます。

`fit!(mach, rows=...)`を使用してマシンをトレーニングします。

# ハイパーパラメータ

  * `normalize=true`: 各クラスの観測数に対するクラス間分散を正規化するオプションで、`true`または`false`のいずれかです。

`outdim`: 出力次元で、`0`の場合は自動的に`min(indim, nclasses-1)`に設定されます。非ゼロの`outdim`が渡された場合、実際に使用される出力次元は`min(rank, outdim)`であり、ここで`rank`はクラス内共分散行列のランクです。

  * `priors::Union{Nothing, UnivariateFinite{<:Any, <:Any, <:Any, <:Real}, Dict{<:Any, <:Real}} = nothing`: ベイズの法則を用いた予測に使用します。`priors = nothing`の場合、`priors`はトレーニングデータのクラス比率から推定されます。そうでない場合、トレーニングターゲット内の非ゼロ確率を持つクラスを指定する`Dict`または`UnivariateFinite`オブジェクトが必要です。

# 操作

  * `transform(mach, Xnew)`: 入力`Xnew`の低次元射影を返します。`X`と同じスカイタイプである必要があります。
  * `predict(mach, Xnew)`: 特徴`Xnew`に基づいてターゲットの予測を返します。`X`と同じスカイタイプである必要があります。予測は確率的ですが、キャリブレーションされていません。
  * `predict_mode(mach, Xnew)`: 上記で返された確率的予測のモードを返します。

# フィッティングパラメータ

`fitted_params(mach)`のフィールドは次のとおりです。

  * `classes`: モデルフィッティング中に見られたクラス。
  * `projection_matrix`: 学習された射影行列で、サイズは`(indim, outdim)`です。ここで`indim`と`outdim`はそれぞれ入力次元と出力次元です（下記のレポートセクションを参照）。
  * `priors`: 分類のためのクラス事前分布。ユーザーが指定しない場合、トレーニングターゲット`y`から推測されます。`levels(y)`と一致するレベルを持つ`UnivariateFinite`オブジェクト。

# レポート

`report(mach)`のフィールドは次のとおりです。

  * `indim`: 入力空間の次元、すなわちトレーニング特徴の数。
  * `outdim`: モデルが射影される変換空間の次元。
  * `mean`: トレーニングデータの全体的な平均。
  * `nclasses`: トレーニングデータで直接観察されたクラスの数（クラスプール内の総クラス数より少ない場合があります）。

`class_means`: トレーニングデータのクラス特有の平均。サイズ`(indim, nclasses)`の行列で、i列目は`classes`のiクラスのクラス平均です（上記のフィッティングパラメータセクションを参照）。

  * `class_weights`: 各クラスの重み（クラスカウント）。長さ`nclasses`のベクトルで、i要素は`classes`のiクラスのクラス重みです（上記のフィッティングパラメータセクションを参照）。
  * `explained_variance_ratio`: 説明された分散と総分散の比率。各次元は固有値に対応します。

# 例

```
using MLJ

BayesianSubspaceLDA = @load BayesianSubspaceLDA pkg=MultivariateStats

X, y = @load_iris # テーブルとベクトル

model = BayesianSubspaceLDA()
mach = machine(model, X, y) |> fit!

Xproj = transform(mach, X)
y_hat = predict(mach, X)
labels = predict_mode(mach, X)
```

[`LDA`](@ref)、[`BayesianLDA`](@ref)、[`SubspaceLDA`](@ref)も参照してください。
