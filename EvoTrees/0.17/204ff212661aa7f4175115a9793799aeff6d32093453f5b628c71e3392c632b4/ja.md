EvoTreeClassifier(;kwargs...)

[EvoTrees.jl](https://github.com/Evovest/EvoTrees.jl)に基づいてEvoTreeClassifierを構築するためのモデルタイプであり、内部APIとMLJモデルインターフェースの両方を実装しています。EvoTreeClassifierは、クロスエントロピー損失を使用して多クラス分類を実行するために使用されます。

# ハイパーパラメータ

  * `early_stopping_rounds::Integer`: メトリックの改善がない連続ラウンドの数。この数に達するとフィッティングが停止します。
  * `nrounds=100`:           ラウンドの数。これは、順次スタックされる木の数に対応します。1以上でなければなりません。
  * `eta=0.1`:              学習率。各木の生の予測は、予測のスタックに追加される前に`eta`でスケーリングされます。0より大きくなければなりません。`eta`が低いほど学習は遅くなり、より高い`nrounds`が必要ですが、通常はモデルのパフォーマンスが向上します。
  * `L2::T=0.0`:            集約ゲインに対するL2正則化係数。0以上でなければなりません。L2が高いほど、より堅牢なモデルが得られる可能性があります。
  * `lambda::T=0.0`:        個別ゲインに対するL2正則化係数。0以上でなければなりません。lambdaが高いほど、より堅牢なモデルが得られる可能性があります。
  * `gamma::T=0.0`:         ノード分割を行うために必要な最小ゲイン改善。gammaが高いほど、より堅牢なモデルが得られる可能性があります。0以上でなければなりません。
  * `max_depth=6`:          木の最大深さ。1以上でなければなりません。深さ1の木は単一の予測リーフで構成されます。深さNの完全な木は`2^(N - 1)`の端末リーフと`2^(N - 1) - 1`の分割ノードを含みます。計算コストは`2^max_depth`に比例します。典型的な最適値は3から9の範囲です。
  * `min_weight=1.0`:       分割を行うためにノードに必要な最小重み。デフォルトでは観測数に一致するか、`weights`ベクターによって提供された重みの合計です。0より大きくなければなりません。
  * `rowsample=1.0`:        木を構築するために各イテレーションでサンプリングされる行の割合。`]0, 1]`の範囲である必要があります。
  * `colsample=1.0`:        木を構築するために各イテレーションでサンプリングされる列/特徴の割合。`]0, 1]`の範囲である必要があります。
  * `nbins=64`:             各特徴が量子化されるビンの数。ビンは分位数に基づいて定義されるため、等しい重みのビンが得られます。2から255の間である必要があります。
  * `tree_type=:binary`    使用する木の構造。次のいずれかです：

      * `:binary`:       木の各ノードは独立して成長します。木は最大深さに達するまで深さ優先で構築されるか、最小重みまたはゲイン（`gamma`を参照）がさらなるノード分割を停止します。
      * `:oblivious`:    特定の深さのすべてのノードに共通の分割条件が課されます。
  * `rng=123`:              乱数生成器へのシードとして使用される整数、または実際の乱数生成器（`::Random.AbstractRNG`）。
  * `device=:cpu`: 計算に使用するハードウェアデバイス。`:cpu`または`:gpu`のいずれかである必要があります。

# 内部API

デフォルトのハイパーパラメータでインスタンスを構築するには`config = EvoTreeClassifier()`を実行します。ハイパーパラメータのデフォルトをオーバーライドするには、`EvoTreeClassifier(max_depth=...)`のようにキーワード引数を提供します。

## モデルのトレーニング

モデルは[`fit_evotree`](@ref)を使用して構築されます：

```julia
model = fit_evotree(config; x_train, y_train, kwargs...)
```

## 推論

予測は[`predict`](@ref)を使用して取得され、`[nobs, K]`のサイズの`Matrix`を返します。ここで`K`はクラスの数です：

```julia
EvoTrees.predict(model, X)
```

または、モデルはファンクタとして機能し、特徴を引数として関数として呼び出すと予測を返します：

```julia
model(X)
```

# MLJ

MLJからは、次のようにタイプをインポートできます：

```julia
EvoTreeClassifier = @load EvoTreeClassifier pkg=EvoTrees
```

デフォルトのハイパーパラメータでインスタンスを構築するには`model = EvoTreeClassifier()`を実行します。ハイパーパラメータのデフォルトをオーバーライドするには、`EvoTreeClassifier(loss=...)`のようにキーワード引数を提供します。

## トレーニングデータ

MLJまたはMLJBaseでは、次のようにインスタンス`model`をデータにバインドします。

```
mach = machine(model, X, y)
```

ここで

  * `X`: 各列が次のいずれかの要素のscitypesを持つ入力特徴の任意のテーブル（例：`DataFrame`）。列のscitypesは`schema(X)`で確認できます。
  * `y`: ターゲットであり、要素のscitypeが`<:Multiclas`または`<:OrderedFactor`である任意の`AbstractVector`です。scitypeは`scitype(y)`で確認できます。

`fit!(mach, rows=...)`を使用してマシンをトレーニングします。

## 操作

  * `predict(mach, Xnew)`: 特徴`Xnew`に基づいてターゲットの予測を返します。`X`と同じscitypeを持つ必要があります。予測は確率的です。
  * `predict_mode(mach, Xnew)`: 上記の予測のモードを返します。

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
config = EvoTreeClassifier(max_depth=5, nbins=32, nrounds=100)
nobs, nfeats = 1_000, 5
x_train, y_train = randn(nobs, nfeats), rand(1:3, nobs)
model = fit_evotree(config; x_train, y_train)
preds = EvoTrees.predict(model, x_train)
```

```
# MLJインターフェース
using MLJ
EvoTreeClassifier = @load EvoTreeClassifier pkg=EvoTrees
model = EvoTreeClassifier(max_depth=5, nbins=32, nrounds=100)
X, y = @load_iris
mach = machine(model, X, y) |> fit!
preds = predict(mach, X)
preds = predict_mode(mach, X)
```

詳細は[EvoTrees.jl](https://github.com/Evovest/EvoTrees.jl)を参照してください。
