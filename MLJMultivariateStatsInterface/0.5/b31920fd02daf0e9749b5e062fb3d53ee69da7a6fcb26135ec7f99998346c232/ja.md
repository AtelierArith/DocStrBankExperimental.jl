```
MultitargetRidgeRegressor
```

マルチターゲットリッジ回帰器を構築するためのモデルタイプで、[MultivariateStats.jl](https://github.com/JuliaStats/MultivariateStats.jl)に基づいており、MLJモデルインターフェースを実装しています。

MLJからは、次のようにタイプをインポートできます。

```
MultitargetRidgeRegressor = @load MultitargetRidgeRegressor pkg=MultivariateStats
```

`model = MultitargetRidgeRegressor()`を実行して、デフォルトのハイパーパラメータを持つインスタンスを構築します。ハイパーパラメータのデフォルトを上書きするには、`MultitargetRidgeRegressor(lambda=...)`のようにキーワード引数を提供します。

マルチターゲットリッジ回帰は、正則化のためにマルチターゲット最小二乗回帰に二次ペナルティ項を追加します。リッジ回帰は、多重共線性のケースで特に有用です。この場合、出力は応答ベクトルを表します。バイアス項を指定し、ペナルティ項の強さを調整するオプションがあります。

# トレーニングデータ

MLJまたはMLJBaseでは、次のようにインスタンス`model`をデータにバインドします。

```
mach = machine(model, X, y)
```

ここで：

  * `X`は、列がスカイタイプ`Continuous`の入力特徴の任意のテーブル（例：`DataFrame`）です。列のスカイタイプは`schema(X)`で確認できます。
  * `y`は、要素のスカイタイプが`Continuous`の応答の任意のテーブルです。スカイタイプは`scitype(y)`で確認できます。

`fit!(mach, rows=...)`を使用してマシンをトレーニングします。

# ハイパーパラメータ

  * `lambda=1.0`: 正則化強度のための非負パラメータです。lambdaが0の場合、リッジ回帰は線形最小二乗回帰と同等であり、lambdaが無限大に近づくと、すべての線形係数は0に近づきます。
  * `bias=true`: trueの場合はバイアス項を含め、そうでない場合はバイアス項なしでフィットします。

# 操作

  * `predict(mach, Xnew)`: 新しい特徴`Xnew`に対するターゲットの予測を返します。`X`と同じスカイタイプである必要があります。

# フィッティングパラメータ

`fitted_params(mach)`のフィールドは次のとおりです。

  * `coefficients`: モデルによって決定された線形係数。
  * `intercept`: モデルによって決定された切片。

# 例

```
using MLJ
using DataFrames

RidgeRegressor = @load MultitargetRidgeRegressor pkg=MultivariateStats

X, y = make_regression(100, 6; n_targets = 2)  # テーブルとテーブル（合成データ）

ridge_regressor = RidgeRegressor(lambda=1.5)
mach = machine(ridge_regressor, X, y) |> fit!

Xnew, _ = make_regression(3, 6)
yhat = predict(mach, Xnew) # 新しい予測
```

[`LinearRegressor`](@ref)、[`MultitargetLinearRegressor`](@ref)、[`RidgeRegressor`](@ref)も参照してください。
