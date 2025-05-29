```julia
function predict(model  :: MDMmodel,
                 𝐏Te    :: ℍVector,
                 what   :: Symbol = :labels;
        pipeline    :: Union{Pipeline, Nothing} = nothing,
        verbose     :: Bool = true,
        ⏩          :: Bool = true)
```

与えられた [`MDM`](@ref) `model` は *z* クラスで訓練（フィッティング）され、*k* 個の正定値行列 `𝐏Te` のテストセットは [ℍVector](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#%E2%84%8DVector-type-1) 型です：

`what` が `:labels` または `:l`（デフォルト）の場合、`𝐏Te` の各行列に対する予測された **クラスラベル** を [IntVector](@ref) として返します。MDM モデルの場合、ラベルのない行列の予測クラス 'ラベル' は、その行列に最も近い平均のクラスのシリアル番号です（平均への最小距離）。クラス 1 のラベルは '1'、クラス 2 のラベルは '2' などです。

`what` が `:probabilities` または `:p` の場合、`𝐏Te` の各行列がすべてのクラスに属する予測された **確率** を、実数を保持する *k* ベクトルの *z* ベクトルとして返します。'確率' は、各ラベルのない行列からすべてのクラスの平均までの二乗距離を逆符号で [ソフトマックス関数](https://en.wikipedia.org/wiki/Softmax_function) に渡すことで得られます。

`what` が `:f` または `:functions` の場合、モデルの **出力関数** を実数を保持する *k* ベクトルの *z* ベクトルとして返します。`𝐏Te` の各要素の関数は、各クラスからの二乗距離の比率であり、すべてのクラスからの二乗距離の（スカラー）幾何平均に対するものです。

`verbose` が true（デフォルト）の場合、情報が REPL に印刷されます。

`⏩` が true（デフォルト）の場合、距離の計算はマルチスレッドで行われます。

提供された `model` のフィールド `pipeline` が `nothing` でない場合、すなわち前処理パイプラインがフィッティングされていることを意味し、予測を行う前にデータにパイプラインが適用されます。テストデータに **適応** したい場合は、モデルのパイプラインを上書きしてテストデータにパイプラインをフィットさせるだけです。これは、クロスセッションおよびクロスサブジェクトの設定で便利です。

!!! warning "パイプラインの適応"
    パイプラインを適応させる際は注意が必要です。もし [`Recenter`](@ref) コンディショナーがパイプラインに含まれていて、次元削減が求められた場合（パラメータ `eVar` が `nothing` でない）、`eVar` は適応後にトレーニングデータとテストデータの次元が同じになるように整数に設定する必要があります。以下の例を参照してください。


**参照**: [表記法と命名法](@ref), [ℍVector 型](@ref)

**関連**: [`fit`](@ref), [`crval`](@ref), [`predictErr`](@ref)

**例**

```julia
using PosDefManifoldML, PosDefManifold

# データを生成
PTr, PTe, yTr, yTe = gen2ClassData(10, 30, 40, 60, 80)

# MDM モデルを作成してフィット
m = fit(MDM(Fisher), PTr, yTr)

# ラベルを予測
yPred = predict(m, PTe, :l)

# 予測誤差
predErr = predictErr(yTe, yPred)

# 確率を予測
predict(m, PTe, :p)

# 出力関数
predict(m, PTe, :f)

# パイプラインの使用と適応

# 例としてランダムデータとラベルを取得
PTr, PTe, yTr, yTe = gen2ClassData(10, 30, 40, 60, 80)

# 適応のために、`eVar` を整数または `nothing` に設定する必要があります。
# トレーニングデータで決定された次元を使用します。
# トレーニングデータのクラスの割合がテストデータのクラスの割合と異なる場合、適応はうまく機能しません。
p = @→ Recenter(; eVar=0.999) Compress Shrink(Fisher; radius=0.02)

# 前処理パイプラインを使用してモデルをフィット
m = fit(MDM(), PTr, yTr; pipeline = p)

# 固定次元削減パラメータで同じパイプラインを定義
p = @→ Recenter(; eVar=dim(m.pipeline)) Compress Shrink(Fisher; radius=0.02)

# テストデータにパイプラインをフィット（適応）：
predict(m, PTe, :l; pipeline=p) 

# 再センタリングを適応させたいが、縮小はしたくない場合、こちらのパイプラインを使用します：
p = deepcopy(m.pipeline)
p[1].eVar = dim(m.pipeline)
```
