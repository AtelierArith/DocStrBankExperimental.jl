```
Stack(; metalearner=nothing, name1=model1, name2=model2, ..., keyword_options...)
```

[Wolpert (1992)](https://www.sciencedirect.com/science/article/abs/pii/S0893608005800231)によって導入され、[Van der Laan et al (2007)](https://biostats.bepress.com/ucbbiostat/paper222/)によって一般化された二層一般化スタックアルゴリズムを実装します。`metalearner`の予測タイプに応じて、`ProbabilisticStack`または`DeterministicStack`のインスタンスを返します。

このインスタンスにバインドされた機械をトレーニングする際には：

  * データは指定された`resampling`戦略に従ってトレーニング/バリデーションセットに分割されます。
  * 各ベースモデル`model1`、`model2`、...は各トレーニングサブセットでトレーニングされ、対応するバリデーションセットに対して予測を出力します。マルチフォールド予測は、各モデルのためのいわゆるアウトオブサンプル予測に結合されます。
  * 裁定モデル`metalearner`は、その後、アウトオブサンプル予測に基づいてトレーニングされ、ベースモデル予測の最良の組み合わせを学習します。
  * 各ベースモデルは、新しい生産データを裁定者に渡して新しい予測を行う目的のために、提供されたすべてのデータで再トレーニングされます。

### 引数

  * `metalearner::Supervised`: その内部に基づいて所望の基準を最適化するモデル。たとえば、LinearRegressionモデルは二乗誤差を最適化します。
  * `resampling`: ベース学習者のアウトオブサンプル予測を準備するために使用されるリサンプリング戦略。
  * `measures`: スタック内の学習者の内部評価を行うための測定または測定のイテラブル。これはスタック自体の評価のためではありません。
  * `cache`: 学習ネットワーク内で作成された機械がデータをキャッシュするかどうか。
  * `acceleration`: スタックのトレーニング並列化モードを定義するためのサポートされた`AbstractResource`。
  * `name1=model1, name2=model2, ...`: ベース学習者として使用される`Supervised`モデルインスタンス。提供された名前は、ハイパーパラメータアクセスを可能にするために作成されたインスタンスのプロパティになります。

### 例

以下のコードは、`Continuous`ターゲットを学習するための`DeterministicStack`インスタンスを定義し、次のことを示します：

  * ベースモデルは、スタック自体が`Deterministic`であっても`Probabilistic`モデルであることができます（その場合、`predict_mean`が適用されます）。
  * ハイパーパラメータ最適化の代替として、与えられたモデルの複数のコピーをスタックし、各コピーで使用されるハイパーパラメータを変更することができます。

```julia
using MLJ

DecisionTreeRegressor = @load DecisionTreeRegressor pkg=DecisionTree
EvoTreeRegressor = @load EvoTreeRegressor
XGBoostRegressor = @load XGBoostRegressor
KNNRegressor = @load KNNRegressor pkg=NearestNeighborModels
LinearRegressor = @load LinearRegressor pkg=MLJLinearModels

X, y = make_regression(500, 5)

stack = Stack(;metalearner=LinearRegressor(),
                resampling=CV(),
                measures=rmse,
                constant=ConstantRegressor(),
                tree_2=DecisionTreeRegressor(max_depth=2),
                tree_3=DecisionTreeRegressor(max_depth=3),
                evo=EvoTreeRegressor(),
                knn=KNNRegressor(),
                xgb=XGBoostRegressor())

mach = machine(stack, X, y)
evaluate!(mach; resampling=Holdout(), measure=rmse)

```

内部評価レポートは次のようにアクセスでき、各モデルのPerformanceEvaluationオブジェクトを提供します：

```julia
report(mach).cv_report
```
