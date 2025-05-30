```
LinearRegressor
```

線形回帰器を構築するためのモデルタイプで、[MultivariateStats.jl](https://github.com/JuliaStats/MultivariateStats.jl)に基づいており、MLJモデルインターフェースを実装しています。

MLJからは、次のようにしてタイプをインポートできます。

```
LinearRegressor = @load LinearRegressor pkg=MultivariateStats
```

`model = LinearRegressor()`を実行して、デフォルトのハイパーパラメータを持つインスタンスを構築します。ハイパーパラメータのデフォルトを上書きするには、`LinearRegressor(bias=...)`のようにキーワード引数を提供します。

`LinearRegressor`はターゲットが`Continuous`変数であると仮定し、最小二乗法を使用して線形予測関数を訓練します。バイアス項を指定するオプションがあります。

# 訓練データ

MLJまたはMLJBaseでは、次のようにしてデータにインスタンス`model`をバインドします。

```
mach = machine(model, X, y)
```

ここで：

  * `X`は、列が`Continuous`のscitypeを持つ任意の入力特徴のテーブル（例：`DataFrame`）です。列のscitypeは`schema(X)`で確認できます。
  * `y`は、要素のscitypeが`Continuous`である任意の`AbstractVector`です。scitypeは`scitype(y)`で確認できます。

`fit!(mach, rows=...)`を使用してマシンを訓練します。

# ハイパーパラメータ

  * `bias=true`: trueの場合はバイアス項を含め、そうでない場合はバイアス項なしでフィットします。

# 操作

  * `predict(mach, Xnew)`: 新しい特徴`Xnew`を考慮したターゲットの予測を返します。`X`と同じscitypeである必要があります。

# フィッティングパラメータ

`fitted_params(mach)`のフィールドは次のとおりです。

  * `coefficients`: モデルによって決定された線形係数。
  * `intercept`: モデルによって決定された切片。

# 例

```
using MLJ

LinearRegressor = @load LinearRegressor pkg=MultivariateStats
linear_regressor = LinearRegressor()

X, y = make_regression(100, 2) # テーブルとベクトル（合成データ）
mach = machine(linear_regressor, X, y) |> fit!

Xnew, _ = make_regression(3, 2)
yhat = predict(mach, Xnew) # 新しい予測
```

[`MultitargetLinearRegressor`](@ref)、[`RidgeRegressor`](@ref)、[`MultitargetRidgeRegressor`](@ref)も参照してください。
