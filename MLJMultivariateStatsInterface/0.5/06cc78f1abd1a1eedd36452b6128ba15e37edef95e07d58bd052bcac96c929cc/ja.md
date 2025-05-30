```
LDA
```

線形判別分析モデルを構築するためのモデルタイプで、[MultivariateStats.jl](https://github.com/JuliaStats/MultivariateStats.jl)に基づき、MLJモデルインターフェースを実装しています。

MLJからは、次のようにしてタイプをインポートできます。

```
LDA = @load LDA pkg=MultivariateStats
```

`model = LDA()`を実行して、デフォルトのハイパーパラメータを持つインスタンスを構築します。ハイパーパラメータのデフォルトを上書きするには、`LDA(method=...)`のようにキーワード引数を提供します。

[多クラス線形判別分析](https://en.wikipedia.org/wiki/Linear_discriminant_analysis)は、離散的なターゲット変数のクラスをできるだけ多く識別できるように、特徴の空間から低次元空間への投影を学習します。これは、特徴の次元削減（下記の`transform`を参照）やターゲットの確率的分類（下記の`predict`を参照）に使用できます。

予測の場合、新しい観測値のクラス確率は、その観測値がそのクラスに関連するトレーニング観測値にどれだけ近いか、またその観測値が他のクラスに関連する観測値からどれだけ離れているかを反映します。具体的には、変換された（投影された）空間における新しい観測値から各ターゲットクラスの重心までの距離が計算されます。その結果得られた距離ベクトルにマイナス1を掛けてソフトマックス関数に渡し、クラス確率の予測を得ます。ここで「距離」は、ユーザー指定の距離関数を使用して計算されます。

# トレーニングデータ

MLJまたはMLJBaseでは、次のようにしてデータにインスタンス`model`をバインドします。

```
mach = machine(model, X, y)
```

ここで：

  * `X`は、列が`Continuous`のscitypeを持つ任意の入力特徴のテーブル（例：`DataFrame`）です。列のscitypesは`schema(X)`で確認できます。
  * `y`は、要素のscitypeが`OrderedFactor`または`Multiclass`である任意の`AbstractVector`です。scitypeは`scitype(y)`で確認できます。

`fit!(mach, rows=...)`を使用してマシンをトレーニングします。

# ハイパーパラメータ

  * `method::Symbol=:gevd`: ソルバー、`:gevd`または`:whiten`メソッドのいずれか。
  * `cov_w::StatsBase.SimpleCovariance()`: クラス内共分散の推定量（クラス内散布行列`Sw`の計算に使用）。`CovarianceEstimation.jl`からの任意のロバスト推定量を使用できます。
  * `cov_b::StatsBase.SimpleCovariance()`: `cov_w`と同じですが、クラス間共分散（クラス間散布行列`Sb`の計算に使用）用です。
  * `outdim::Int=0`: 出力次元、すなわち変換された空間の次元で、0の場合は自動的に`min(indim, nclasses-1)`に設定されます。
  * `regcoef::Float64=1e-6`: 正則化係数。正の値`regcoef*eigmax(Sw)`（ここで`Sw`はクラス内散布行列）が`Sw`の対角に追加され、数値的安定性が向上します。これは、標準共分散推定器を使用する場合に便利です。
  * `dist=Distances.SqEuclidean()`: 分類を行う際に使用する距離メトリック（新しい点と変換空間の重心との距離を比較するため）。`Distances.jl`の`Distances.SemiMetric`のサブタイプでなければなりません。例：`Distances.CosineDist`。

# 操作

  * `transform(mach, Xnew)`: 入力`Xnew`の低次元投影を返します。`X`と同じscitypeを持つ必要があります。
  * `predict(mach, Xnew)`: 特徴`Xnew`に基づいてターゲットの予測を返します。`X`と同じscitypeを持つ必要があります。予測は確率的ですが、キャリブレーションされていません。
  * `predict_mode(mach, Xnew)`: 上記で返された確率的予測のモードを返します。

# フィッティングパラメータ

`fitted_params(mach)`のフィールドは次のとおりです。

  * `classes`: モデルフィッティング中に見られたクラス。
  * `projection_matrix`: 学習された投影行列、サイズは`(indim, outdim)`で、`indim`と`outdim`はそれぞれ入力次元と出力次元です（下記のレポートセクションを参照）。

# レポート

`report(mach)`のフィールドは次のとおりです。

  * `indim`: 入力空間の次元、すなわちトレーニング特徴の数。
  * `outdim`: モデルが投影される変換空間の次元。
  * `mean`: 変換されていないトレーニングデータの平均。長さ`indim`のベクトル。
  * `nclasses`: トレーニングデータで直接観察されたクラスの数（クラスプールの総クラス数より少ない場合があります）。
  * `class_means`: トレーニングデータのクラス特有の平均。サイズ`(indim, nclasses)`の行列で、i列は`classes`のiクラスのクラス平均です（上記のフィッティングパラメータセクションを参照）。
  * `class_weights`: 各クラスの重み（クラス数）。長さ`nclasses`のベクトルで、i要素は`classes`のiクラスのクラス重みです（上記のフィッティングパラメータセクションを参照）。
  * `Sb`: クラス間散布行列。
  * `Sw`: クラス内散布行列。

# 例

```
using MLJ

LDA = @load LDA pkg=MultivariateStats

X, y = @load_iris # テーブルとベクトル

model = LDA()
mach = machine(model, X, y) |> fit!

Xproj = transform(mach, X)
y_hat = predict(mach, X)
labels = predict_mode(mach, X)

```

[`BayesianLDA`](@ref)、[`SubspaceLDA`](@ref)、[`BayesianSubspaceLDA`](@ref)も参照してください。
