NeuroTreeRegressor(; kwargs...)

[NeuroTreeModels.jl](https://github.com/Evovest/NeuroTreeModels.jl)に基づいて、NeuroTreeRegressorを構築するためのモデルタイプであり、内部APIとMLJモデルインターフェースの両方を実装しています。

# ハイパーパラメータ

  * `loss=:mse`:              トレーニング中に最小化される損失。次のいずれかの値を取ります：

      * `:mse`
      * `:mae`
      * `:logloss`
      * `:gaussian_mle`
  * `metric=nothing`: `deval`で追跡される評価指標。次のいずれかの値を取ります：

      * `:mse`
      * `:mae`
      * `:logloss`
      * `:gaussian_mle`
  * `nrounds=100`:            最大ラウンド数（エポック）。
  * `lr=1.0f-2`:              学習率。0より大きくなければなりません。`eta`が低いほど学習は遅くなり、通常はより高い`nrounds`が必要です。
  * `wd=0.f0`:                オプティマイザによって勾配に適用される重み減衰。
  * `batchsize=2048`:         バッチサイズ。
  * `actA=:tanh`:             分割ノードの重みを決定するために各入力変数に適用される活性化関数。次のいずれかの値を取ります：

      * `:tanh`
      * `:identity`
  * `depth=6`:                木の深さ。1以上でなければなりません。深さ1の木は2つの予測リーフノードを持ちます。深さNの完全な木は`2^N`の端末リーフと`2^N - 1`の分割ノードを含みます。計算コストは`2^depth`に比例します。典型的な最適値は3から5の範囲です。
  * `ntrees=64`:              木の数（スタックごと）。
  * `hidden_size=16`:         隠れ層のサイズ。`stack_size` > 1のときのみ適用されます。
  * `stack_size=1`:           スタックされたNeuroTreeブロックの数。
  * `scaler=true`:            シグモイド活性化の前に学習可能なスケーリング係数を使用するかどうか。そうでない場合、`scaler=false`の場合は1.0の固定スケーリングが使用されます。
  * `init_scale=0.1`:         予測重みに適用されるスケーリング係数。範囲`]0, 1]`の値は最良の収束をもたらすはずです。
  * `MLE_tree_split=false`:   `gaussian_mle`損失の2つのパラメータ（mu、sigma）ごとに独立したモデルが構築されるかどうか。
  * `rng=123`:                ランダム数生成器のシードとして使用される整数、または実際のランダム数生成器（`::Random.AbstractRNG`）。
  * `device=:cpu`:            計算を実行するデバイス、`:cpu`または`:gpu`のいずれか。
  * `gpuID=0`:                使用するGPUデバイス、`device = :gpu`の場合のみ関連します。

# 内部API

デフォルトのハイパーパラメータでインスタンスを構築するには`config = NeuroTreeRegressor()`を実行します。ハイパーパラメータのデフォルトを上書きするには、`NeuroTreeRegressor(loss=:logloss, depth=5, ...)`のようにキーワード引数を提供します。

## モデルのトレーニング

モデルは[`fit`](@ref)を使用してトレーニングされます：

```julia
m = fit(config, dtrain; feature_names, target_name, kwargs...)
```

## 推論

モデルはファンクタとして機能し、特徴を引数として関数として呼び出すと予測を返します：

```julia
m(data)
```

# MLJインターフェース

MLJからは、次のようにしてタイプをインポートできます：

```julia
NeuroTreeRegressor = @load NeuroTreeRegressor pkg=NeuroTreeModels
```

デフォルトのハイパーパラメータでインスタンスを構築するには`model = NeuroTreeRegressor()`を実行します。ハイパーパラメータのデフォルトを上書きするには、`NeuroTreeRegressor(loss=...)`のようにキーワード引数を提供します。

## モデルのトレーニング

MLJまたはMLJBaseでは、`mach = machine(model, X, y)`を使用してインスタンス`model`をデータにバインドします。ここで

  * `X`: 各列が次のいずれかの要素のscitypesを持つ入力特徴の任意のテーブル（例：`DataFrame`）。列のscitypesは`schema(X)`で確認できます。
  * `y`: ターゲットであり、要素のscitypeが`<:Continuous`である任意の`AbstractVector`です。scitypeは`scitype(y)`で確認できます。

`fit!(mach, rows=...)`を使用してマシンをトレーニングします。

## 操作

  * `predict(mach, Xnew)`: 特徴`Xnew`に基づいてターゲットの予測を返します。`X`と同じscitypeを持つ必要があります。

## フィッティングパラメータ

`fitted_params(mach)`のフィールドは次のとおりです：

  * `:fitresult`: `NeuroTreeModel`オブジェクト。

## レポート

`report(mach)`のフィールドは次のとおりです：

  * `:features`: トレーニング中に遭遇した特徴の名前。

# 例

## 内部API

```julia
using NeuroTreeModels, DataFrames
config = NeuroTreeRegressor(depth=5, nrounds=10)
nobs, nfeats = 1_000, 5
dtrain = DataFrame(randn(nobs, nfeats), :auto)
dtrain.y = rand(nobs)
feature_names, target_name = names(dtrain, r"x"), "y"
m = fit(config, dtrain; feature_names, target_name)
p = m(dtrain)
```

## MLJインターフェース

```julia
using MLJBase, NeuroTreeModels
m = NeuroTreeRegressor(depth=5, nrounds=10)
X, y = @load_boston
mach = machine(m, X, y) |> fit!
p = predict(mach, X)
```
