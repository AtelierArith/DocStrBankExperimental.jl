EvoTreeRegressor(;kwargs...)

[EvoTrees.jl](https://github.com/Evovest/EvoTrees.jl)に基づいてEvoTreeRegressorを構築するためのモデルタイプで、内部APIとMLJモデルインターフェースの両方を実装しています。

# ハイパーパラメータ

  * `loss=:mse`:         トレーニング中に最小化される損失。次のいずれかの値を取ります：

      * `:mse`
      * `:mae`
      * `:logloss`
      * `:gamma`
      * `:tweedie`
      * `:quantile`
      * `:cred_var`: **実験的** 信用に基づく利益で、スプレッドとプロセスの分散の比率から導出されます。
      * `:cred_std`: **実験的** 信用に基づく利益で、スプレッドとプロセスの標準偏差の比率から導出されます。
  * `metric`:     評価データを追跡するために使用され、早期停止の基準となる評価指標。サポートされている指標は次のとおりです：

      * `:mse`:     平均二乗誤差。一般的な回帰モデルに適応されています。
      * `:rmse`:    平均二乗根誤差。一般的な回帰モデルに適応されています。
      * `:mae`:     平均絶対誤差。一般的な回帰モデルに適応されています。
      * `:logloss`: `:logistic`回帰モデルに適応されています。
      * `:poisson`: ポアソン偏差。`EvoTreeCount`カウントモデルに適応されています。
      * `:gamma`:   ガンマ偏差。ガンマのような正に分布されたターゲットに対する回帰問題に適応されています。
      * `:tweedie`: ツイーディー偏差。`y == 0`で確率質量を持つツイーディーのような正に分布されたターゲットに対する回帰問題に適応されています。
      * `:quantile`: 非対称絶対誤差に対応し、残差はその符号に応じてalpha / (1-alpha)に従ってペナルティが課されます。
      * `:gini`: 予測とターゲットの間の正規化されたジニ
  * `early_stopping_rounds::Integer`: メトリックの改善がない連続ラウンドの数で、その後フィッティングが停止されます。
  * `nrounds=100`:           ラウンドの数。これは、順次スタックされる木の数に対応します。1以上でなければなりません。
  * `eta=0.1`:              学習率。各木の生の予測は、予測のスタックに追加される前に`eta`でスケーリングされます。0より大きくなければなりません。`eta`が低いほど学習が遅くなり、より高い`nrounds`が必要ですが、通常はモデルのパフォーマンスが向上します。
  * `L2::T=0.0`:            集約利益に対するL2正則化係数。0以上でなければなりません。高いL2は、より堅牢なモデルをもたらす可能性があります。
  * `lambda::T=0.0`:        個別利益に対するL2正則化係数。0以上でなければなりません。高いlambdaは、より堅牢なモデルをもたらす可能性があります。
  * `gamma::T=0.0`:         ノード分割を行うために必要な最小利益改善。高いgammaは、より堅牢なモデルをもたらす可能性があります。0以上でなければなりません。
  * `alpha::T=0.5`:         [0, 1]の範囲内の損失特有のパラメータ：                           - `:quantile`: 回帰のためのターゲット分位数。
  * `max_depth=6`:          木の最大深さ。1以上でなければなりません。深さ1の木は単一の予測リーフで構成されます。深さNの完全な木は`2^(N - 1)`の端末リーフと`2^(N - 1) - 1`の分割ノードを含みます。計算コストは`2^max_depth`に比例します。典型的な最適値は3から9の範囲です。
  * `min_weight=1.0`:       分割を行うためにノードに必要な最小重み。デフォルトでは観測数と一致するか、`weights`ベクトルによって提供された重みの合計です。0より大きくなければなりません。
  * `rowsample=1.0`:        木を構築するために各イテレーションでサンプリングされる行の割合。`]0, 1]`の範囲内である必要があります。
  * `colsample=1.0`:        木を構築するために各イテレーションでサンプリングされる列/特徴の割合。`]0, 1]`の範囲内である必要があります。
  * `nbins=64`:             各特徴が量子化されるビンの数。ビンは分位数に基づいて定義されるため、等しい重みのビンが得られます。2から255の間である必要があります。
  * `monotone_constraints=Dict{Int, Int}()`: 辞書を使用して単調制約を指定します。キーは特徴インデックスで、値は適用可能な制約（-1=減少、0=なし、1=増加）です。現在のところ、`：linear`、`：logistic`、`：gamma`および`tweedie`損失のみがサポートされています。
  * `tree_type=:binary`    使用する木の構造。次のいずれかの値を取ります：

      * `:binary`:       木の各ノードは独立して成長します。木は最大深さに達するまで、または最小重みまたは利益（`gamma`を参照）がさらなるノード分割を停止するまで深さ優先で構築されます。
      * `:oblivious`:    特定の深さのすべてのノードに共通の分割条件が課されます。
  * `rng=123`:              ランダム数生成器へのシードとして使用される整数、または実際のランダム数生成器（`::Random.AbstractRNG`）。
  * `device=:cpu`: 計算に使用するハードウェアデバイス。`:cpu`または`gpu`のいずれかである必要があります。

# 内部API

`config = EvoTreeRegressor()`を実行して、デフォルトのハイパーパラメータでインスタンスを構築します。キーワード引数を提供してハイパーパラメータのデフォルトを上書きします（例：`EvoTreeRegressor(loss=...)`）。

## モデルのトレーニング

モデルは[`fit_evotree`](@ref)を使用して構築されます：

```julia
model = fit_evotree(config; x_train, y_train, kwargs...)
```

## 推論

予測は[`predict`](@ref)を使用して取得され、`nobs`の長さの`Vector`を返します：

```julia
EvoTrees.predict(model, X)
```

または、モデルはファンクタとして機能し、特徴を引数として関数として呼び出すと予測を返します：

```julia
model(X)
```

# MLJインターフェース

MLJからは、次のようにしてタイプをインポートできます：

```julia
EvoTreeRegressor = @load EvoTreeRegressor pkg=EvoTrees
```

`model = EvoTreeRegressor()`を実行して、デフォルトのハイパーパラメータでインスタンスを構築します。キーワード引数を提供してハイパーパラメータのデフォルトを上書きします（例：`EvoTreeRegressor(loss=...)`）。

## モデルのトレーニング

MLJまたはMLJBaseでは、`mach = machine(model, X, y)`を使用してデータにインスタンス`model`をバインドします。ここで、

  * `X`: 各列が次のいずれかの要素のscitypesを持つ入力特徴の任意のテーブル（例：`DataFrame`）です：`Continuous`、`Count`、または`<:OrderedFactor`。`schema(X)`を使用して列のscitypesを確認します。
  * `y`: ターゲットで、要素のscitypeが`<:Continuous`である任意の`AbstractVector`です。`scitype(y)`を使用してscitypeを確認します。

`fit!(mach, rows=...)`を使用してマシンをトレーニングします。

## 操作

  * `predict(mach, Xnew)`: 上記の`X`と同じscitypeを持つ特徴`Xnew`が与えられたときのターゲットの予測を返します。予測は決定論的です。

## フィッティングされたパラメータ

`fitted_params(mach)`のフィールドは次のとおりです：

  * `:fitresult`: EvoTrees.jlフィッティングアルゴリズムによって返される`GBTree`オブジェクト。

## レポート

`report(mach)`のフィールドは次のとおりです：

  * `:features`: トレーニング中に遭遇した特徴の名前。

# 例

```
# 内部API
using EvoTrees
config = EvoTreeRegressor(max_depth=5, nbins=32, nrounds=100)
nobs, nfeats = 1_000, 5
x_train, y_train = randn(nobs, nfeats), rand(nobs)
model = fit_evotree(config; x_train, y_train)
preds = EvoTrees.predict(model, x_train)
```

```
# MLJインターフェース
using MLJ
EvoTreeRegressor = @load EvoTreeRegressor pkg=EvoTrees
model = EvoTreeRegressor(max_depth=5, nbins=32, nrounds=100)
X, y = @load_boston
mach = machine(model, X, y) |> fit!
preds = predict(mach, X)
```
