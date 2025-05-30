```
SubspaceLDA
```

サブスペースLDAモデルを構築するためのモデルタイプで、[MultivariateStats.jl](https://github.com/JuliaStats/MultivariateStats.jl)に基づいており、MLJモデルインターフェースを実装しています。

MLJからは、次のようにタイプをインポートできます。

```
SubspaceLDA = @load SubspaceLDA pkg=MultivariateStats
```

`model = SubspaceLDA()`を実行して、デフォルトのハイパーパラメータを持つインスタンスを構築します。ハイパーパラメータのデフォルトを上書きするには、`SubspaceLDA(normalize=...)`のようにキーワード引数を提供します。

多クラスサブスペース線形判別分析（LDA）は、通常の[`LDA`](@ref)の変種であり、高次元データに適しており、散布行列を保存することを避けます。詳細については、[MultivariateStats.jlのドキュメント](https://juliastats.org/MultivariateStats.jl/stable/)を参照してください。

次元削減（`transform`を使用）に加えて、確率的分類も提供されます（`predict`を使用）。分類の場合、新しい観測値のクラス確率は、その観測値がそのクラスに関連するトレーニング観測値にどれだけ近いか、またその観測値が他のクラスに関連する観測値からどれだけ離れているかを反映します。具体的には、変換された（投影された）空間における新しい観測値から各ターゲットクラスの重心までの距離が計算されます。得られた距離のベクトルはマイナス1倍され、ソフトマックス関数に渡されてクラス確率の予測が得られます。ここで「距離」は、ユーザー指定の距離関数を使用して計算されます。

# トレーニングデータ

MLJまたはMLJBaseでは、次のようにインスタンス`model`をデータにバインドします。

```
mach = machine(model, X, y)
```

ここで：

  * `X`は、列がスカイタイプ`Continuous`の任意の入力特徴のテーブル（例：`DataFrame`）です。列のスカイタイプは`schema(X)`で確認できます。
  * `y`は、要素のスカイタイプが`OrderedFactor`または`Multiclass`である任意の`AbstractVector`です。スカイタイプは`scitype(y)`で確認できます。

`fit!(mach, rows=...)`を使用してマシンをトレーニングします。

# ハイパーパラメータ

  * `normalize=true`: 各クラスの観測数に対するクラス間分散を正規化するオプションで、`true`または`false`のいずれかです。
  * `outdim`: 出力次元で、`0`の場合は自動的に`min(indim, nclasses-1)`に設定されます。非ゼロの`outdim`が渡された場合、実際に使用される出力次元は`min(rank, outdim)`であり、ここで`rank`はクラス内共分散行列のランクです。
  * `dist=Distances.SqEuclidean()`: 分類を行う際に使用する距離メトリック（新しい点と変換空間の重心との距離を比較するため）。`Distances.jl`の`Distances.SemiMetric`のサブタイプでなければなりません。例：`Distances.CosineDist`。

# 操作

  * `transform(mach, Xnew)`: 入力`Xnew`の低次元投影を返します。`X`と同じスカイタイプである必要があります。
  * `predict(mach, Xnew)`: 特徴`Xnew`に基づいてターゲットの予測を返します。`X`と同じスカイタイプである必要があります。予測は確率的ですが、キャリブレーションされていません。
  * `predict_mode(mach, Xnew)`: 上記で返された確率的予測のモードを返します。

# フィッティングパラメータ

`fitted_params(mach)`のフィールドは次のとおりです。

  * `classes`: モデルフィッティング中に見られたクラス。
  * `projection_matrix`: 学習された投影行列で、サイズは`(indim, outdim)`です。ここで`indim`と`outdim`はそれぞれ入力次元と出力次元です（下記のレポートセクションを参照）。

# レポート

`report(mach)`のフィールドは次のとおりです。

  * `indim`: 入力空間の次元、すなわちトレーニング特徴の数。
  * `outdim`: モデルが投影される変換空間の次元。
  * `mean`: 変換されていないトレーニングデータの平均。長さ`indim`のベクトル。
  * `nclasses`: トレーニングデータで直接観測されたクラスの数（クラスプール内の総クラス数より少ない場合があります）

`class_means`: トレーニングデータのクラス特有の平均。サイズ`(indim, nclasses)`の行列で、i列は`classes`のiクラスのクラス平均です（上記のフィッティングパラメータセクションを参照）。

  * `class_weights`: 各クラスの重み（クラス数）。長さ`nclasses`のベクトルで、i要素は`classes`のiクラスのクラス重みです（上記のフィッティングパラメータセクションを参照）。
  * `explained_variance_ratio`: 説明された分散と総分散の比率。各次元は固有値に対応します。

# 例

```
using MLJ

SubspaceLDA = @load SubspaceLDA pkg=MultivariateStats

X, y = @load_iris # テーブルとベクトル

model = SubspaceLDA()
mach = machine(model, X, y) |> fit!

Xproj = transform(mach, X)
y_hat = predict(mach, X)
labels = predict_mode(mach, X)
```

他にも[`LDA`](@ref)、[`BayesianLDA`](@ref)、[`BayesianSubspaceLDA`](@ref)を参照してください。
