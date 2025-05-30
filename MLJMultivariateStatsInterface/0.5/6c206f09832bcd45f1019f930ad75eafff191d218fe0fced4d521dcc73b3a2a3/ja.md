```
MultitargetLinearRegressor
```

マルチターゲット線形回帰器を構築するためのモデルタイプで、[MultivariateStats.jl](https://github.com/JuliaStats/MultivariateStats.jl)に基づいており、MLJモデルインターフェースを実装しています。

MLJからは、次のようにしてタイプをインポートできます。

```
MultitargetLinearRegressor = @load MultitargetLinearRegressor pkg=MultivariateStats
```

`model = MultitargetLinearRegressor()`を実行して、デフォルトのハイパーパラメータを持つインスタンスを構築します。ハイパーパラメータのデフォルトを上書きするには、`MultitargetLinearRegressor(bias=...)`のようにキーワード引数を提供します。

`MultitargetLinearRegressor`は、ターゲット変数が連続成分を持つベクトル値であることを前提としています。最小二乗法を使用して線形予測関数を訓練します。バイアス項を指定するオプションがあります。

# トレーニングデータ

MLJまたはMLJBaseでは、次のようにしてデータにインスタンス`model`をバインドします。

```
mach = machine(model, X, y)
```

ここで：

  * `X`は、列がscitype `Continuous`である任意の入力特徴のテーブル（例：`DataFrame`）です。列のscitypeは`schema(X)`で確認できます。
  * `y`は、要素のscitypeが`Continuous`である任意の応答のテーブルです。scitypeは`scitype(y)`で確認できます。

`fit!(mach, rows=...)`を使用してマシンを訓練します。

# ハイパーパラメータ

  * `bias=true`: trueの場合はバイアス項を含め、そうでない場合はバイアス項なしでフィットします。

# 操作

  * `predict(mach, Xnew)`: 新しい特徴`Xnew`に対するターゲットの予測を返します。`X`と同じscitypeである必要があります。

# フィッティングパラメータ

`fitted_params(mach)`のフィールドは次のとおりです。

  * `coefficients`: モデルによって決定された線形係数。
  * `intercept`: モデルによって決定された切片。

# 例

```
using MLJ
using DataFrames

LinearRegressor = @load MultitargetLinearRegressor pkg=MultivariateStats
linear_regressor = LinearRegressor()

X, y = make_regression(100, 9; n_targets = 2) # テーブルとテーブル（合成データ）

mach = machine(linear_regressor, X, y) |> fit!

Xnew, _ = make_regression(3, 9)
yhat = predict(mach, Xnew) # 新しい予測
```

[`LinearRegressor`](@ref)、[`RidgeRegressor`](@ref)、[`MultitargetRidgeRegressor`](@ref)も参照してください。
