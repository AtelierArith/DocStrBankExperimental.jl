```
ImageClassifier
```

画像分類器を構築するためのモデルタイプで、[MLJFlux.jl](https://github.com/alan-turing-institute/MLJFlux.jl)に基づき、MLJモデルインターフェースを実装しています。

MLJからは、次のようにしてタイプをインポートできます。

```
ImageClassifier = @load ImageClassifier pkg=MLJFlux
```

`model = ImageClassifier()`を実行して、デフォルトのハイパーパラメータでインスタンスを構築します。ハイパーパラメータのデフォルトを上書きするには、`ImageClassifier(builder=...)`のようにキーワード引数を提供します。

`ImageClassifier`は、提供された画像のタイプ（カラーまたはグレースケール）に適応したニューラルネットワークを使用して画像を分類します。予測は確率的です。ユーザーは、遭遇した画像の特性に基づいてネットワークを構築するためのレシピを提供し、適切な`builder`を指定します。ビルダーに関する詳細はMLJFluxのドキュメントを参照してください。

# トレーニングデータ

MLJまたはMLJBaseでは、次のようにしてデータにインスタンス`model`をバインドします。

```
mach = machine(model, X, y)
```

ここで：

  * `X`は、`ColorImage`または`GrayImage`のscitypeを持つ任意の`AbstractVector`の画像です。`scitype(X)`でscitypeを確認し、典型的な画像フォーマットを適切なタイプに強制する方法についてはScientificTypes.jlのドキュメントを参照してください。
  * `y`はターゲットで、要素のscitypeが`Multiclass`である任意の`AbstractVector`です。`scitype(y)`でscitypeを確認します。

`fit!(mach, rows=...)`を使用してマシンをトレーニングします。

# ハイパーパラメータ

  * `builder`: ニューラルネットワークを構築するMLJFluxビルダー。フォールバックは、画像サイズとターゲットクラスの数に適応した深さ16のVGGアーキテクチャを構築し、バッチ正規化は行いません。詳細についてはMetalhead.jlのドキュメントを参照してください。ユーザー指定のビルダーの例は以下に示します。便利なマクロ`@builder`も利用可能です。以下の`finaliser`も参照してください。
  * `optimiser::Optimisers.Adam()`: Optimisers.jlのオプティマイザ。オプティマイザはネットワークの重みの更新を行います。学習率（オプティマイザの更新率）を選択するための良いルールは、`10e-3`から始め、`1`と`1e-7`の間の10の累乗を使用して調整することです。
  * `loss=Flux.crossentropy`: ネットワークが最適化する損失関数。`loss(yhat, y)`の形式で呼び出せる関数である必要があります。可能な損失関数は[Fluxの損失関数のドキュメント](https://fluxml.ai/Flux.jl/stable/models/losses/)にリストされています。分類タスクにおいて最も自然な損失関数は次のとおりです：

      * `Flux.crossentropy`: 標準的なマルチクラス分類損失、別名ログ損失。
      * `Flux.logitcrossentopy`: 数学的にはクロスエントロピーと等しいが、出力を`softmax`で最終化してからクロスエントロピーを計算するよりも数値的に安定しています。MLJFluxのデフォルトのsoftmaxファイナライザーを削除するために`finaliser=identity`を指定する必要があり、`predict`の出力はその後正規化されていない（確率的でなくなる）ことを理解してください。
      * `Flux.tversky_loss`: 不均衡データで使用され、偽陰性により多くの重みを与えます。
      * `Flux.focal_loss`: 非常に不均衡なデータで使用され、難しい例により多くの重みを与えます。

    現在、MLJの測定値は`loss`の値としてサポートされていません。
  * `epochs::Int=10`: エポックでのトレーニングの期間。通常、1エポックはトレーニングデータセット全体を1回通過することを表します。
  * `batch_size::int=1`: トレーニングに使用されるバッチサイズで、ネットワークの重みの更新ごとのサンプル数を表します。通常、バッチサイズは8から512の間です。

    バッチサイズを増やすことで、`acceleration=CUDALibs()`が指定され、GPUが利用可能な場合、トレーニングが加速される可能性があります。
  * `lambda::Float64=0`: 重みの正則化ペナルティの強さ。範囲は`[0, ∞)`の任意の値を取ることができます。履歴はペナルティなしの損失を報告します。
  * `alpha::Float64=0`: 正則化のL2/L1ミックスで、範囲は`[0, 1]`です。0の値はL2正則化を表し、1の値はL1正則化を表します。
  * `rng::Union{AbstractRNG, Int64}`: トレーニング中に使用される乱数生成器またはシード。デフォルトは`Random.default_rng()`です。
  * `optimizer_changes_trigger_retraining::Bool=false`: 関連するオプティマイザが変更された場合にマシンを再フィッティングするときに何が起こるかを定義します。`true`の場合、関連するマシンは`fit!`呼び出し時に最初から再トレーニングされます。それ以外の場合は再トレーニングされません。
  * `acceleration::AbstractResource=CPU1()`: トレーニングが行われるハードウェアを定義します。GPUでのトレーニングには`CUDALibs()`を使用します。
  * `finaliser=Flux.softmax`: ニューラルネットワークの最終的な活性化関数（`builder`で定義されたネットワークの後に適用されます）。デフォルトは`Flux.softmax`です。

# 操作

  * `predict(mach, Xnew)`: 新しい特徴`Xnew`に対するターゲットの予測を返します。`X`と同じscitypeを持つ必要があります。予測は確率的ですが、キャリブレーションされていません。
  * `predict_mode(mach, Xnew)`: 上記で返された確率的予測のモードを返します。

# フィッティングされたパラメータ

`fitted_params(mach)`のフィールドは次のとおりです：

  * `chain`: トレーニングされた「チェーン」（Flux.jlモデル）、すなわちニューラルネットワークを構成する層、関数、および活性化の系列。これには、`finaliser`（例：`softmax`）で指定された最終層が含まれます。

# レポート

`report(mach)`のフィールドは次のとおりです：

  * `training_losses`: 歴史的順序でのトレーニング損失のベクトル（`lambda != 0`の場合はペナルティ付き）、長さは`epochs + 1`です。最初の要素はプレトレーニング損失です。

# 例

この例では、MLJFluxとカスタムビルダーを使用してMNIST画像データセットを分類します。

```julia
using MLJ
using Flux
import MLJFlux
import Optimisers
import MLJIteration # for `skip` control
```

まず、MNISTデータセットをダウンロードし、画像とラベルに展開します。

```julia
import MLDatasets: MNIST
data = MNIST(split=:train)
images, labels = data.features, data.targets
```

MLJでは、整数はカテゴリデータのエンコーディングに使用できないため、`Multiclass`のscitypeに強制する必要があります。

```julia
labels = coerce(labels, Multiclass);
```

上記の`images`は単一の配列ですが、MLJFluxは画像を個々の画像配列のベクトルとして要求します。

```
images = coerce(images, GrayImage);
images[1]
```

適切な`builder`オブジェクトを定義することから始めます。これはニューラルネットワークを構築するためのレシピです。私たちのビルダーは、カラーまたは白黒（すなわち、単一または複数チャネル）のいずれの（定数）サイズの画像にも対応します。アーキテクチャは常に6つの交互の畳み込み層とマックスプール層、そして最終的な密な層で構成され、各畳み込み層のフィルターサイズとチャネル数はカスタマイズ可能です。

```julia
import MLJFlux

struct MyConvBuilder
    filter_size::Int
    channels1::Int
    channels2::Int
    channels3::Int
end

make2d(x::AbstractArray) = reshape(x, :, size(x)[end])

function MLJFlux.build(b::MyConvBuilder, rng, n_in, n_out, n_channels)
    k, c1, c2, c3 = b.filter_size, b.channels1, b.channels2, b.channels3
    mod(k, 2) == 1 || error("`filter_size` must be odd. ")
    p = div(k - 1, 2) # 画像サイズを保持するためのパディング
    init = Flux.glorot_uniform(rng)
    front = Chain(
        Conv((k, k), n_channels => c1, pad=(p, p), relu, init=init),
        MaxPool((2, 2)),
        Conv((k, k), c1 => c2, pad=(p, p), relu, init=init),
        MaxPool((2, 2)),
        Conv((k, k), c2 => c3, pad=(p, p), relu, init=init),
        MaxPool((2 ,2)),
        make2d)
    d = Flux.outputsize(front, (n_in..., n_channels, 1)) |> first
    return Chain(front, Dense(d, n_out, init=init))
end
```

私たちの`build`関数では、最終的な`softmax`がないことに注意することが重要です。これは、すべてのMLJFlux分類器でデフォルトで適用されます（`finaliser`ハイパーパラメータを使用してこれを上書きできます）。

ビルダーが定義されたので、実際のMLJFluxモデルをインスタンス化できます。GPUがある場合は、トレーニングを加速するために以下の`acceleration=CUDALibs()`を代入できます。

```julia
ImageClassifier = @load ImageClassifier pkg=MLJFlux
clf = ImageClassifier(builder=MyConvBuilder(3, 16, 32, 32),
                      batch_size=50,
                      epochs=10,
                      rng=123)
```

上記のスニペットに`optimiser`や`loss`などのFluxオプションを追加できます。現在、`loss`はflux互換の損失でなければなりません。

次に、データとともにマシンにモデルをバインドし、最初の500画像を使用してトレーニングします。

```julia
mach = machine(clf, images, labels);
fit!(mach, rows=1:500, verbosity=2);
report(mach)
chain = fitted_params(mach)
Flux.params(chain)[2]
```

`epochs`フィールドを変更してさらに20エポックを追加し、さらにフィットさせることができます。

```julia
clf.epochs = clf.epochs + 20
fit!(mach, rows=1:500, verbosity=2);
```

予測を行い、任意のMLJ測定値（損失/スコア）を使用してサンプル外の損失推定を計算することもできます。

```julia
predicted_labels = predict(mach, rows=501:1000);
cross_entropy(predicted_labels, labels[501:1000])
```

前述の`fit!`/`predict`/evaluateワークフローは、次のように代替して実行できます。

```julia
evaluate!(mach,
          resampling=Holdout(fraction_train=0.5),
          measure=cross_entropy,
          rows=1:1000,
          verbosity=0)
```

[`NeuralNetworkClassifier`](@ref)も参照してください。
