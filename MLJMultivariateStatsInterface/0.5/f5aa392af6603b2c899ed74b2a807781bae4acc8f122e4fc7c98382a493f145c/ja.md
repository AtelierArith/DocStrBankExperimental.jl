```
BayesianLDA
```

ベイズLDAモデルを構築するためのモデルタイプで、[MultivariateStats.jl](https://github.com/JuliaStats/MultivariateStats.jl)に基づいており、MLJモデルインターフェースを実装しています。

MLJからは、次のようにしてタイプをインポートできます。

```
BayesianLDA = @load BayesianLDA pkg=MultivariateStats
```

`model = BayesianLDA()`を実行して、デフォルトのハイパーパラメータを持つインスタンスを構築します。ハイパーパラメータのデフォルトを上書きするには、`BayesianLDA(method=...)`のようにキーワード引数を提供します。

ベイズ多クラスLDAアルゴリズムは、通常の[`LDA`](@ref)で説明されているように、射影行列を学習します。予測されたクラスの事後確率分布は、多変量ガウス分布のクラス条件付き分布を用いてベイズの法則を適用することによって導出されます。事前のクラス分布は、ユーザーによって指定するか、トレーニングデータのクラス頻度から推測されます。

詳細については、[パッケージのドキュメント](https://multivariatestatsjl.readthedocs.io/en/latest/lda.html)も参照してください。アルゴリズムに関する詳細は、[Li, Zhu and Ogihara (2006): Using Discriminant Analysis for Multi-class Classification: An Experimental Investigation](https://doi.org/10.1007/s10115-006-0013-y)を参照してください。

# トレーニングデータ

MLJまたはMLJBaseでは、次のようにしてインスタンス`model`をデータにバインドします。

```
mach = machine(model, X, y)
```

ここで：

  * `X`は、列が`Continuous`のscitypeを持つ任意の入力特徴のテーブル（例：`DataFrame`）です。列のscitypeは`schema(X)`で確認できます。
  * `y`は、要素のscitypeが`OrderedFactor`または`Multiclass`である任意の`AbstractVector`です。scitypeは`scitype(y)`で確認できます。

`fit!(mach, rows=...)`を使用してマシンをトレーニングします。

# ハイパーパラメータ

  * `method::Symbol=:gevd`: ソルバーの選択、`:gevd`または`:whiten`メソッドのいずれか。
  * `cov_w::StatsBase.SimpleCovariance()`: クラス内共分散の推定量（クラス内散布行列`Sw`の計算に使用）。`CovarianceEstimation.jl`の任意のロバスト推定量を使用できます。
  * `cov_b::StatsBase.SimpleCovariance()`: `cov_w`と同じですが、クラス間共分散（クラス間散布行列`Sb`の計算に使用）用です。
  * `outdim::Int=0`: 出力次元、すなわち変換された空間の次元で、0の場合は自動的に`min(indim, nclasses-1)`に設定されます。
  * `regcoef::Float64=1e-6`: 正則化係数。正の値`regcoef*eigmax(Sw)`（ここで`Sw`はクラス内散布行列）が`Sw`の対角に追加され、数値的安定性を向上させます。これは、標準共分散推定量を使用する場合に便利です。
  * `priors::Union{Nothing, UnivariateFinite{<:Any, <:Any, <:Any, <:Real}, Dict{<:Any, <:Real}} = nothing`: ベイズの法則による予測に使用します。`priors = nothing`の場合、`priors`はトレーニングデータのクラス比率から推定されます。そうでない場合、トレーニングターゲットにおいて非ゼロ確率を持つクラスを指定する`Dict`または`UnivariateFinite`オブジェクトが必要です。

# 操作

  * `transform(mach, Xnew)`: 入力`Xnew`の低次元射影を返します。`X`と同じscitypeを持つ必要があります。
  * `predict(mach, Xnew)`: 特徴`Xnew`に基づいてターゲットの予測を返します。`X`と同じscitypeを持つ必要があります。予測は確率的ですが、キャリブレーションされていません。
  * `predict_mode(mach, Xnew)`: 上記で返された確率的予測のモードを返します。

# フィッティングパラメータ

`fitted_params(mach)`のフィールドは次のとおりです。

  * `classes`: モデルフィッティング中に見られたクラス。
  * `projection_matrix`: 学習された射影行列で、サイズは`(indim, outdim)`です。ここで`indim`と`outdim`はそれぞれ入力次元と出力次元です（下記のレポートセクションを参照）。
  * `priors`: 分類のためのクラスの事前分布。ユーザーが指定しない場合、トレーニングターゲット`y`から推測されます。`levels(y)`と一致するレベルを持つ`UnivariateFinite`オブジェクト。

# レポート

`report(mach)`のフィールドは次のとおりです。

  * `indim`: 入力空間の次元、すなわちトレーニング特徴の数。
  * `outdim`: モデルが射影される変換空間の次元。
  * `mean`: 変換されていないトレーニングデータの平均。長さ`indim`のベクトル。
  * `nclasses`: トレーニングデータで直接観察されたクラスの数（クラスプールの総クラス数より少ない場合があります）。
  * `class_means`: トレーニングデータのクラス特有の平均。サイズ`(indim, nclasses)`の行列で、i列目は`classes`のiクラスのクラス平均です（上記のフィッティングパラメータセクションを参照）。
  * `class_weights`: 各クラスの重み（クラスカウント）。長さ`nclasses`のベクトルで、i要素は`classes`のiクラスのクラス重みです（上記のフィッティングパラメータセクションを参照）。
  * `Sb`: クラス間散布行列。
  * `Sw`: クラス内散布行列。

# 例

```
using MLJ

BayesianLDA = @load BayesianLDA pkg=MultivariateStats

X, y = @load_iris # テーブルとベクトル

model = BayesianLDA()
mach = machine(model, X, y) |> fit!

Xproj = transform(mach, X)
y_hat = predict(mach, X)
labels = predict_mode(mach, X)
```

他にも[`LDA`](@ref)、[`SubspaceLDA`](@ref)、[`BayesianSubspaceLDA`](@ref)を参照してください。
