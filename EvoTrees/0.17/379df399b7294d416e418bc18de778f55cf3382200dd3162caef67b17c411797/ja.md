EvoTreeGaussian(;kwargs...)

[EvoTrees.jl](https://github.com/Evovest/EvoTrees.jl)に基づいてEvoTreeGaussianを構築するためのモデルタイプであり、内部APIとMLJモデルインターフェースの両方を実装しています。EvoTreeGaussianは、μとσパラメータをフィッティングして尤度を最大化するために、ガウス確率回帰を実行するために使用されます。

# ハイパーパラメータ

  * `early_stopping_rounds::Integer`: メトリックの改善がない連続したラウンドの数で、これを超えるとフィッティングが停止します。
  * `nrounds=100`:           ラウンドの数。これは、順次スタックされる木の数に対応します。1以上でなければなりません。
  * `eta=0.1`:              学習率。各木の生の予測は、予測のスタックに追加される前に`eta`でスケーリングされます。0より大きくなければなりません。`eta`が低いほど学習は遅くなり、より高い`nrounds`が必要ですが、通常はモデルのパフォーマンスが向上します。
  * `L2::T=0.0`:            集約ゲインに対するL2正則化係数。0以上でなければなりません。L2が高いほど、より堅牢なモデルが得られる可能性があります。
  * `lambda::T=0.0`:        個別ゲインに対するL2正則化係数。0以上でなければなりません。lambdaが高いほど、より堅牢なモデルが得られる可能性があります。
  * `gamma::T=0.0`:         ノード分割を行うために必要な最小ゲインの改善。gammaが高いほど、より堅牢なモデルが得られる可能性があります。0以上でなければなりません。
  * `max_depth=6`:          木の最大深さ。1以上でなければなりません。深さ1の木は単一の予測リーフで構成されます。深さNの完全な木は`2^(N - 1)`の端末リーフと`2^(N - 1) - 1`の分割ノードを含みます。計算コストは2^max_depthに比例します。典型的な最適値は3から9の範囲にあります。
  * `min_weight=8.0`:       分割を行うためにノードに必要な最小重み。デフォルトでは観測数に一致するか、`weights`ベクターによって提供された重みの合計です。0より大きくなければなりません。
  * `rowsample=1.0`:        木を構築するために各イテレーションでサンプリングされる行の割合。`]0, 1]`の範囲である必要があります。
  * `colsample=1.0`:        木を構築するために各イテレーションでサンプリングされる列/特徴の割合。`]0, 1]`の範囲である必要があります。
  * `nbins=64`:             各特徴が量子化されるビンの数。ビンは分位数に基づいて定義されるため、等しい重みのビンが得られます。2から255の間である必要があります。
  * `monotone_constraints=Dict{Int, Int}()`: 特徴インデックスがキーで、適用可能な制約（-1=減少、0=なし、1=増加）が値である辞書を使用して単調制約を指定します。！実験的な機能：ガウス回帰の場合、制約が体系的に強制されない可能性があることに注意してください。
  * `tree_type=:binary`    使用する木の構造。次のいずれかです：

      * `:binary`:       木の各ノードは独立して成長します。木は最大深さに達するまで深さ優先で構築されるか、最小重みまたはゲイン（`gamma`を参照）がさらなるノード分割を停止します。
      * `:oblivious`:    特定の深さのすべてのノードに共通の分割条件が課されます。
  * `rng=123`:              ランダム数生成器へのシードとして使用される整数、または実際のランダム数生成器（`::Random.AbstractRNG`）。
  * `device=:cpu`: 計算に使用するハードウェアデバイス。`:cpu`または`gpu`のいずれかである必要があります。

# 内部API

デフォルトのハイパーパラメータでインスタンスを構築するには`config = EvoTreeGaussian()`を実行します。ハイパーパラメータのデフォルトをオーバーライドするには、EvoTreeGaussian(max_depth=...)のようにキーワード引数を提供します。

## モデルのトレーニング

モデルは[`fit_evotree`](@ref)を使用して構築されます：

```julia
model = fit_evotree(config; x_train, y_train, kwargs...)
```

## 推論

予測は[`predict`](@ref)を使用して取得され、`[nobs, 2]`のサイズの`Matrix`を返します。ここで、2次元はそれぞれ`μ`と`σ`を指します：

```julia
EvoTrees.predict(model, X)
```

または、モデルはファンクタとして機能し、特徴を引数として関数として呼び出すと予測を返します：

```julia
model(X)
```

# MLJ

MLJからは、次のようにしてタイプをインポートできます：

```julia
EvoTreeGaussian = @load EvoTreeGaussian pkg=EvoTrees
```

デフォルトのハイパーパラメータでインスタンスを構築するには`model = EvoTreeGaussian()`を実行します。ハイパーパラメータのデフォルトをオーバーライドするには、`EvoTreeGaussian(loss=...)`のようにキーワード引数を提供します。

## トレーニングデータ

MLJまたはMLJBaseでは、次のようにしてデータにインスタンス`model`をバインドします。

```
mach = machine(model, X, y)
```

ここで

  * `X`: 各列が次のいずれかの要素のscitypesを持つ入力特徴の任意のテーブル（例：`DataFrame`）です：`Continuous`、`Count`、または`<:OrderedFactor`。`schema(X)`で列のscitypesを確認します。
  * `y`: ターゲットであり、要素のscitypeが`<:Continuous`である任意の`AbstractVector`です。`scitype(y)`でscitypeを確認します。

`fit!(mach, rows=...)`を使用してマシンをトレーニングします。

## 操作

  * `predict(mach, Xnew)`: 特徴`Xnew`に基づいてガウス分布のベクトルを返します。`X`と同じscitypeを持つ必要があります。

予測は確率的です。

特定のメトリックも次のようにして予測できます：

  * `predict_mean(mach, Xnew)`
  * `predict_mode(mach, Xnew)`
  * `predict_median(mach, Xnew)`

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
params = EvoTreeGaussian(max_depth=5, nbins=32, nrounds=100)
nobs, nfeats = 1_000, 5
x_train, y_train = randn(nobs, nfeats), rand(nobs)
model = fit_evotree(params; x_train, y_train)
preds = EvoTrees.predict(model, x_train)
```

```
# MLJインターフェース
using MLJ
EvoTreeGaussian = @load EvoTreeGaussian pkg=EvoTrees
model = EvoTreeGaussian(max_depth=5, nbins=32, nrounds=100)
X, y = @load_boston
mach = machine(model, X, y) |> fit!
preds = predict(mach, X)
preds = predict_mean(mach, X)
preds = predict_mode(mach, X)
preds = predict_median(mach, X)
```
