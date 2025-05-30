```
RidgeRegressor
```

リッジ回帰器を構築するためのモデルタイプで、[MultivariateStats.jl](https://github.com/JuliaStats/MultivariateStats.jl)に基づいており、MLJモデルインターフェースを実装しています。

MLJからは、次のようにしてタイプをインポートできます。

```
RidgeRegressor = @load RidgeRegressor pkg=MultivariateStats
```

`model = RidgeRegressor()`を実行して、デフォルトのハイパーパラメータでインスタンスを構築します。ハイパーパラメータのデフォルトをオーバーライドするには、`RidgeRegressor(lambda=...)`のようにキーワード引数を提供します。

`RidgeRegressor`は、最小二乗回帰に二次ペナルティ項を追加して正則化を行います。リッジ回帰は特に多重共線性のケースで有用です。バイアス項を指定するオプションや、ペナルティ項の強さを調整するオプションがあります。

# トレーニングデータ

MLJまたはMLJBaseでは、次のようにしてインスタンス`model`をデータにバインドします。

```
mach = machine(model, X, y)
```

ここで：

  * `X`は、列がスカイタイプ`Continuous`である任意の入力特徴のテーブル（例：`DataFrame`）です。列のスカイタイプは`schema(X)`で確認できます。
  * `y`は、要素のスカイタイプが`Continuous`である任意の`AbstractVector`です。スカイタイプは`scitype(y)`で確認できます。

`fit!(mach, rows=...)`を使用してマシンをトレーニングします。

# ハイパーパラメータ

  * `lambda=1.0`: 正則化の強さのための非負パラメータです。lambdaが0の場合、リッジ回帰は線形最小二乗回帰と同等であり、lambdaが無限大に近づくと、すべての線形係数は0に近づきます。
  * `bias=true`: trueの場合はバイアス項を含め、そうでない場合はバイアス項なしでフィットします。

# 操作

  * `predict(mach, Xnew)`: 新しい特徴`Xnew`に基づいてターゲットの予測を返します。`X`と同じスカイタイプである必要があります。

# フィッティングされたパラメータ

`fitted_params(mach)`のフィールドは次のとおりです。

  * `coefficients`: モデルによって決定された線形係数。
  * `intercept`: モデルによって決定された切片。

# 例

```
using MLJ

RidgeRegressor = @load RidgeRegressor pkg=MultivariateStats
pipe = Standardizer() |> RidgeRegressor(lambda=10)

X, y = @load_boston

mach = machine(pipe, X, y) |> fit!
yhat = predict(mach, X)
training_error = l1(yhat, y) |> mean
```

[`LinearRegressor`](@ref)、[`MultitargetLinearRegressor`](@ref)、[`MultitargetRidgeRegressor`](@ref)も参照してください。
