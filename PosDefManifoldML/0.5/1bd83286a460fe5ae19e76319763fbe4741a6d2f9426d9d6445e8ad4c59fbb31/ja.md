```julia
function predict(model   :: ENLRmodel,
		𝐏Te         :: Union{ℍVector, Matrix{Float64}},
		what        :: Symbol = :labels,
		fitType     :: Symbol = :best,
		onWhich     :: Int    = Int(fitType==:best);
    pipeline    :: Union{Pipeline, Nothing} = nothing,
    meanISR     :: Union{ℍ, Nothing, UniformScaling} = nothing,
    verbose     :: Bool = true,
    ⏩          :: Bool = true)
```

与えられた[`ENLR`](@ref) `model`は2クラスで訓練（フィット）され、テストセットは* k *の正定値行列`𝐏Te`の型[ℍVector](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#%E2%84%8DVector-type-1)です。

`what`が`:labels`または`:l`（デフォルト）の場合、`𝐏Te`内の各行列に対する予測された**クラスラベル**を[IntVector](@ref)として返します。これらのラベルはクラス1に対して'1'、クラス2に対して'2'です。

`what`が`:probabilities`または`:p`の場合、`𝐏Te`内の各行列が各クラスに属する確率を予測した**確率**を返します。これは、*k*-ベクトルの*z*ベクトルとして、* [0, 1] *（確率）内の実数を保持します。'確率'は、ENLRモデルの出力とゼロを[ソフトマックス関数](https://en.wikipedia.org/wiki/Softmax_function)に渡すことで得られます。

`what`が`:f`または`:functions`の場合、モデルの**出力関数**を返します。これはENLRモデルの生の出力です。

`fitType` = `:best`（デフォルト）の場合、交差検証によって見つかった最良のモデルが予測に使用されます。

`fitType` = `:path`の場合、

  * `onWhich`が`model.path`内のモデルの有効なシリアル番号である場合、

このモデルが予測に使用されます。

  * `onWhich`がゼロの場合、`model.path`内のすべてのモデルが予測に使用され、出力は`model.path`内のモデルの数で乗算されます。

引数`onWhich`は、`fitType` = `:best`の場合は効果がありません。

!!! note "Nota Bene"
    デフォルトでは、[`fit`](@ref)関数は`best`モデルのみをフィットします。`fitType` = `:path`オプションを使用したい場合は、オプションのキーワード引数`fitType`=`:path`または`fitType`=`:all`を指定してフィット関数を呼び出す必要があります。詳細については[`fit`](@ref)関数を参照してください。


オプションのキーワード引数`meanISR`は、テストセット`𝐏Te`内の行列を接線空間に投影するための基準点として使用される新しい平均の主逆平方根（ISR）を指定するために使用できます。デフォルトでは`meanISR`は何も指定されていないため、基準点はモデルをフィットするために使用された平均になります。これは古典的な「トレーニング-テスト」動作モードに対応します。

引数`meanISR`に新しい平均ISRを渡すことで、Barachant et *al.*（2013）で最初に説明された*適応*が可能になります。通常、`meanISR`は`𝐏Te`内の行列の平均のISRまたはそのサブセットのISRです。これは、Zanini et *al.*（2018）で定義されたアイデンティティ行列にトレーニングデータとテストデータの両方を平行輸送することによって*転送学習*を実行します。`meanISR=I`を渡すこともできます。この場合、基準点はアイデンティティ行列として取られます。これは、`𝐏Te`セットがアイデンティティに中心化されている場合に可能です。たとえば、再中心化の前処理器がパイプラインに含まれており、パイプラインも適応されている場合です（以下の例を参照）。

`verbose`がtrue（デフォルト）の場合、情報がREPLに印刷されます。このオプションは、REPLを混雑させることなく、この関数を繰り返し呼び出すことを可能にするために含まれています。

`⏩`がtrue（デフォルト）で、`𝐏Te`がℍVector型の場合、接線空間への投影はマルチスレッドで行われます。

提供された`model`のフィールド`pipeline`が`nothing`でない場合、つまりモデルのフィッティング中に前処理パイプラインがフィットされていることを意味し、予測を行う前にデータにパイプラインが適用されます。テストデータにパイプラインを**適応**させたい場合は、この関数の引数`pipeline`に同じパイプラインを渡すだけです。

!!! warning "パイプラインの適応"
    パイプラインを適応させる際は注意が必要です。もし[`Recenter`](@ref)コンディショナーがパイプラインに含まれており、次元削減が求められた場合（パラメータ`eVar`が`nothing`以外）、`eVar`は整数に設定する必要があります。そうしないと、適応後のトレーニングデータとテストデータの次元が同じになりません。以下の例を参照してください。


**参照**: [表記法と命名法](@ref), [ℍVector型](@ref)

**関連**: [`fit`](@ref), [`crval`](@ref), [`predictErr`](@ref)

**例**

```julia
using PosDefManifoldML, PosDefManifold

# データを生成
PTr, PTe, yTr, yTe = gen2ClassData(10, 30, 40, 60, 80)

# ENLRラッソモデルをフィットし、交差検証によって最良のモデルを見つける
m = fit(ENLR(Fisher), PTr, yTr)

# 最良のモデルからラベルを予測
yPred = predict(m, PTe, :l)

# 予測誤差
predErr = predictErr(yTe, yPred)

# 最良のモデルから確率を予測
predict(m, PTe, :p)

# 最良のモデルから出力関数を予測
predict(m, PTe, :f)

# ENLRラッソモデルの正則化パスをフィット
m = fit(ENLR(Fisher), PTr, yTr; fitType=:path)

# 特定のモデルを使用してラベルを予測
yPred = predict(m, PTe, :l, :path, 10)

# すべてのモデルのラベルを予測
yPred = predict(m, PTe, :l, :path, 0)

# すべてのモデルの予測誤差
predErr = [predictErr(yTe, yPred[:, i]) for i=1:size(yPred, 2)]

# 特定のモデルから確率を予測
predict(m, PTe, :p, :path, 12)

# すべてのモデルから確率を予測
predict(m, PTe, :p, :path, 0)

# 特定のモデルから出力関数を予測
predict(m, PTe, :f, :path, 3)

# すべてのモデルの出力関数を予測
predict(m, PTe, :f, :path, 0)

## 基準点の適応
PTr, PTe, yTr, yTe = gen2ClassData(10, 30, 40, 60, 80)
m = fit(ENLR(Fisher), PTr, yTr)
predict(m, PTe, :l; meanISR=invsqrt(mean(Fisher, PTe)))

# 前処理パイプラインを使用して適応
# 適応のためには、`eVar`を整数または`nothing`に設定する必要があります。
# トレーニングデータで決定された次元を使用します。
# トレーニングデータのクラスの割合がテストデータのクラスの割合と異なる場合、適応はうまく機能しないことに注意してください。
p = @→ Recenter(; eVar=0.999) Compress Shrink(Fisher; radius=0.02)

# 前処理パイプラインを使用してモデルをフィット
m = fit(ENLR(), PTr, yTr; pipeline = p)

# 固定次元削減パラメータで同じパイプラインを定義
p = @→ Recenter(; eVar=dim(m.pipeline)) Compress Shrink(Fisher; radius=0.02)

# テストデータにパイプラインをフィット（適応）し、アイデンティティ行列を基準点として使用：
predict(m, PTe, :l; pipeline=p, meanISR=I) 

# 再中心化を適応させたいが、縮小は適応させたくない場合、こちらのパイプラインを使用します：
p = deepcopy(m.pipeline)
p[1].eVar = dim(m.pipeline)
```
