```
NeuroTreeClassifier(; kwargs...)
```

[NeuroTreeModels.jl](https://github.com/Evovest/NeuroTreeModels.jl)に基づいて、NeuroTreeClassifierを構築するためのモデルタイプであり、内部APIとMLJモデルインターフェースの両方を実装しています。

# ハイパーパラメータ

  * `nrounds=100`:             最大ラウンド数（エポック）。
  * `lr=1.0f-2`:              学習率。0より大きくなければならない。`eta`が低いほど学習が遅くなり、通常はより高い`nrounds`が必要です。
  * `wd=0.f0`:                オプティマイザによって勾配に適用される重み減衰。
  * `batchsize=2048`:         バッチサイズ。
  * `actA=:tanh`:             分割ノードの重みを決定するために各入力変数に適用される活性化関数。次のいずれかである必要があります：

      * `:tanh`
      * `:identity`
  * `depth=6`:            木の深さ。1以上でなければならない。深さ1の木は2つの予測リーフノードを持ちます。深さNの完全な木は`2^N`の端末リーフと`2^N - 1`の分割ノードを含みます。計算コストは`2^depth`に比例します。典型的な最適値は3から5の範囲です。
  * `ntrees=64`:              木の数（スタックごと）。
  * `hidden_size=16`:         隠れ層のサイズ。`stack_size` > 1のときのみ適用されます。
  * `stack_size=1`:           スタックされたNeuroTreeブロックの数。
  * `scaler=true`:            シグモイド活性化の前に学習可能なスケーリングファクターを使用するかどうか。そうでない場合、`scaler=false`の場合は1.0の固定スケーリングが使用されます。
  * `init_scale=0.1`:         予測重みに適用されるスケーリングファクター。範囲`]0, 1]`の値は最良の収束をもたらすはずです。
  * `MLE_tree_split=false`:   `gaussian_mle`損失の2つのパラメータ（mu、sigma）ごとに独立したモデルが構築されるかどうか。
  * `rng=123`:                ランダム数生成器へのシードとして使用される整数、または実際のランダム数生成器（`::Random.AbstractRNG`）。
  * `device=:cpu`:            計算を実行するデバイス、`:cpu`または`:gpu`のいずれか。
  * `gpuID=0`:                使用するGPUデバイス、`device = :gpu`の場合のみ関連します。

# 内部API

`config = NeuroTreeClassifier()`を実行して、デフォルトのハイパーパラメータでインスタンスを構築します。ハイパーパラメータのデフォルトをオーバーライドするには、`NeuroTreeClassifier(depth=5, ...)`のようにキーワード引数を提供します。

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
NeuroTreeClassifier = @load NeuroTreeClassifier pkg=NeuroTreeModels
```

`model = NeuroTreeClassifier()`を実行して、デフォルトのハイパーパラメータでインスタンスを構築します。ハイパーパラメータのデフォルトをオーバーライドするには、`NeuroTreeClassifier(loss=...)`のようにキーワード引数を提供します。

## モデルのトレーニング

MLJまたはMLJBaseでは、インスタンス`model`をデータにバインドします。`mach = machine(model, X, y)`のようにします。

  * `X`: 各列が次のいずれかの要素のscitypesを持つ入力特徴の任意のテーブル（例：`DataFrame`）。列のscitypesは`schema(X)`で確認できます。
  * `y`: ターゲットであり、要素のscitypeが`<:Finite`である任意の`AbstractVector`です。scitypeは`scitype(y)`で確認できます。

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
using NeuroTreeModels, DataFrames, CategoricalArrays, Random 
config = NeuroTreeClassifier(depth=5, nrounds=10)
nobs, nfeats = 1_000, 5
dtrain = DataFrame(randn(nobs, nfeats), :auto)
dtrain.y = categorical(rand(1:2, nobs))
feature_names, target_name = names(dtrain, r"x"), "y"
m = fit(config, dtrain; feature_names, target_name)
p = m(dtrain)
```

## MLJインターフェース

```julia
using MLJBase, NeuroTreeModels
m = NeuroTreeClassifier(depth=5, nrounds=10)
X, y = @load_crabs
mach = machine(m, X, y) |> fit!
p = predict(mach, X)
```
