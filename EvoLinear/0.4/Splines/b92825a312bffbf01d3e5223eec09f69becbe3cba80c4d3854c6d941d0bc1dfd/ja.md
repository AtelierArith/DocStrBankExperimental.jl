```
EvoSplineRegressor(; kwargs...)
```

[EvoLinear.jl](https://github.com/jeremiedb/EvoLinear.jl)に基づいてEvoSplineRegressorを構築するためのモデルタイプであり、内部APIとMLJモデルインターフェースの両方を実装しています。

# キーワード引数

  * `loss=:mse`: 最小化される損失関数。次のいずれかである必要があります：

      * `:mse`
      * `:logistic`
      * `:poisson`
      * `:gamma`
      * `:tweedie`
  * `nrounds=10`: 最大トレーニングラウンド数。
  * `eta=1`: 学習率。通常は`[1e-2, 1]`の範囲です。
  * `L1=0`: 更新がL1未満の場合に0に収束させる正則化ペナルティ。更新がL1を超える場合はペナルティなし。スパースな特徴選択をもたらします。通常は正規化された特徴の`[0, 1]`の範囲です。
  * `L2=0`: 重みの更新値の二乗に適用される正則化ペナルティ。大きなパラメータ値を制限します。通常は正規化された特徴の`[0, 1]`の範囲です。
  * `rng=123`: ランダムシード。現時点では使用されていません。
  * `updater=:all`: トレーニングメソッド。現時点では`:all`のみがサポートされています。各特徴の勾配は同時に計算され、その後すべての特徴の更新に基づいてバイアスが更新されます。
  * `device=:cpu`: 現時点では`:cpu`のみがサポートされています。

# 内部API

`config = EvoSplineRegressor()`を実行して、デフォルトのハイパーパラメータを持つハイパーパラメータ構造体を構築します。デフォルトを上書きするために、上記のようにキーワード引数を提供します。例えば：

```julia
EvoSplineRegressor(loss=:logistic, L1=1e-3, L2=1e-2, nrounds=100)
```

## モデルのトレーニング

モデルは[`fit`](@ref)を使用して構築されます：

```julia
config = EvoSplineRegressor()
m = fit(config; x, y, w)
```

## 推論

フィッティングされた結果は、特徴行列を引数として渡すと予測関数として機能する`EvoLinearModel`です。  

```julia
preds = m(x)
```

# MLJインターフェース

MLJからは、次のようにしてタイプをインポートできます：

```julia
EvoSplineRegressor = @load EvoSplineRegressor pkg=EvoLinear
```

`model = EvoLinearRegressor()`を実行して、デフォルトのハイパーパラメータを持つインスタンスを構築します。`EvoSplineRegressor(loss=...)`のように、ハイパーパラメータのデフォルトを上書きするためにキーワード引数を提供します。

## モデルのトレーニング

MLJまたはMLJBaseでは、`mach = machine(model, X, y)`を使用してデータにインスタンス`model`をバインドします。ここで：

  * `X`: 各列が次のいずれかの要素のscitypesを持つ入力特徴の任意のテーブル（例：`DataFrame`）。列のscitypesは`schema(X)`で確認できます。
  * `y`: ターゲットであり、要素のscitypeが`<:Continuous`である任意の`AbstractVector`です。scitypeは`scitype(y)`で確認できます。

`fit!(mach, rows=...)`を使用してマシンをトレーニングします。

## 操作

  * `predict(mach, Xnew)`: 上記の`X`と同じscitypeを持つ特徴`Xnew`が与えられたときのターゲットの予測を返します。予測は決定論的です。

## フィッティングされたパラメータ

`fitted_params(mach)`のフィールドは次のとおりです：

  * `:fitresult`: EvoSplineRegressorフィッティングアルゴリズムによって返される`SplineModel`オブジェクト。

## レポート

`report(mach)`のフィールドは次のとおりです：

  * `:coef`: 各特徴に関連付けられた係数（β）のベクトル。
  * `:bias`: バイアスの値。
  * `:names`: 各特徴の名前。

```
