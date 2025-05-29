```
NeuralNetworkBinaryClassifier
```

ニューラルネットワークバイナリ分類器を構築するためのモデルタイプで、[MLJFlux.jl](https://github.com/alan-turing-institute/MLJFlux.jl)に基づいており、MLJモデルインターフェースを実装しています。

MLJからは、次のようにしてタイプをインポートできます。

```
NeuralNetworkBinaryClassifier = @load NeuralNetworkBinaryClassifier pkg=MLJFlux
```

`model = NeuralNetworkBinaryClassifier()`を実行して、デフォルトのハイパーパラメータでインスタンスを構築します。ハイパーパラメータのデフォルトをオーバーライドするには、`NeuralNetworkBinaryClassifier(builder=...)`のようにキーワード引数を提供します。

`NeuralNetworkBinaryClassifier`は、`Continuous`特徴のテーブルが与えられたときに、バイナリ（`Multiclass{2}`または`OrderedFactor{2}`）ターゲットの確率的予測を行うために、データ依存のFlux.jlニューラルネットワークをトレーニングするためのものです。ユーザーは、遭遇したデータの特性に基づいてネットワークを構築するためのレシピを提供し、適切な`builder`を指定します。ビルダーについての詳細はMLJFluxのドキュメントを参照してください。

`Continuous`科学要素タイプの特徴に加えて、このモデルは入力テーブル内のカテゴリカル特徴もサポートしています。存在する場合、そのような特徴は、入力の後に追加の`EntityEmbedderLayer`レイヤーを使用して密なベクトルに埋め込まれます。これは、Cheng Guo、Felix Berkhahnによる「Categorical Variablesのエンティティ埋め込み」に記載されています。

# トレーニングデータ

MLJまたはMLJBaseでは、次のようにしてインスタンス`model`をデータにバインドします。

```
mach = machine(model, X, y)
```

ここで：

  * `X`は入力特徴を提供し、次のいずれかです：(i) `Continuous`要素のscitypeを持つ`Matrix`（通常は`Float32`）; または (ii) `Continuous`、`Multiclass`または`OrderedFactor`要素のscitypeを持つ入力特徴のテーブル（例：`DataFrame`）; 列のscitypeは`schema(X)`で確認できます。`Multiclass`または`OrderedFactor`特徴が存在する場合、構築されたネットワークはそれらを密なベクトルに変換するために`EntityEmbedderLayer`レイヤーを使用します。`X`が`Matrix`の場合、列は特徴に対応し、行は観測に対応していると見なされます。
  * `y`はターゲットで、要素のscitypeが`Multiclass{2}`または`OrderedFactor{2}`である任意の`AbstractVector`であることができます; `scitype(y)`でscitypeを確認してください。

`fit!(mach, rows=...)`を使用してマシンをトレーニングします。

# ハイパーパラメータ

  * `builder=MLJFlux.Short()`: ニューラルネットワークを構築するMLJFluxビルダー。可能な`builders`には、`MLJFlux.Linear`、`MLJFlux.Short`、および`MLJFlux.MLP`が含まれます。ユーザー定義のビルダーの例については、MLJFlux.jlのドキュメントを参照してください。また、以下の`finaliser`も参照してください。
  * `optimiser::Flux.Adam()`: `Flux.Optimise`オプティマイザー。オプティマイザーはネットワークの重みの更新を行います。詳細については、[Fluxオプティマイザーのドキュメント](https://fluxml.ai/Flux.jl/stable/training/optimisers/)を参照してください。学習率（オプティマイザーの更新率）を選択するための良いルールは、`10e-3`から始め、`1`と`1e-7`の間の`10`の累乗を使用して調整することです。
  * `loss=Flux.binarycrossentropy`: ネットワークが最適化する損失関数。`loss(yhat, y)`の形式で呼び出すことができる関数である必要があります。可能な損失関数は、[Flux損失関数のドキュメント](https://fluxml.ai/Flux.jl/stable/models/losses/)にリストされています。分類タスクにおいて、最も自然な損失関数は次のとおりです：

      * `Flux.binarycrossentropy`: 標準的なバイナリ分類損失、別名ログ損失。
      * `Flux.logitbinarycrossentropy`: 数学的にはクロスエントロピーと等しいが、出力を`σ`で最終化してからクロスエントロピーを計算するよりも数値的に安定しています。`finaliser=identity`を指定してMLJFluxのデフォルトのシグモイドファイナライザーを削除し、`predict`の出力が正規化されていない（確率的でなくなる）ことを理解する必要があります。
      * `Flux.tversky_loss`: 不均衡データで使用され、偽陰性により多くの重みを与えます。
      * `Flux.binary_focal_loss`: 非常に不均衡なデータで使用され、難しい例により多くの重みを与えます。

    現在、MLJの測定値は`loss`の値としてサポートされていません。
  * `epochs::Int=10`: エポックでのトレーニングの期間。通常、1エポックはトレーニングデータセット全体を1回通過することを表します。
  * `batch_size::int=1`: トレーニングに使用されるバッチサイズで、ネットワークの重みの更新ごとのサンプル数を表します。通常、バッチサイズは`8`から`512`の間です。バッチサイズを増やすと、`acceleration=CUDALibs()`でGPUが利用可能な場合、トレーニングが加速される可能性があります。
  * `lambda::Float64=0`: 重みの正則化ペナルティの強さ。範囲`[0, ∞)`の任意の値を取ることができます。
  * `alpha::Float64=0`: 正則化のL2/L1ミックスで、範囲`[0, 1]`の値です。0の値はL2正則化を表し、1の値はL1正則化を表します。
  * `rng::Union{AbstractRNG, Int64}`: トレーニング中に使用される乱数生成器またはシード。
  * `optimizer_changes_trigger_retraining::Bool=false`: 関連するオプティマイザーが変更された場合にマシンを再フィッティングするときに何が起こるかを定義します。`true`の場合、関連するマシンは`fit!`呼び出しで最初から再トレーニングされます。それ以外の場合は再トレーニングされません。
  * `acceleration::AbstractResource=CPU1()`: トレーニングが行われるハードウェアを定義します。GPUでのトレーニングには`CUDALibs()`を使用します。
  * `finaliser=Flux.σ`: ニューラルネットワークの最終活性化関数（`builder`で定義されたネットワークの後に適用されます）。デフォルトは`Flux.σ`です。
  * `embedding_dims`: カテゴリカル特徴の名前をシンボルとしてキーに持ち、そのような特徴のエンティティ埋め込みの望ましい次元を表す数値を値に持つ`Dict`です。例えば、整数値`7`は埋め込みの次元を`7`に設定し、浮動小数点値`0.5`は埋め込みの次元を`ceil(0.5 * c)`に設定します。ここで、`c`は特徴レベルの数です。指定されていない特徴の次元は`min(c - 1, 10)`にデフォルト設定されます。

# 操作

  * `predict(mach, Xnew)`: 新しい特徴`Xnew`が与えられたときのターゲットの予測を返します。`X`と同じscitypeを持つ必要があります。予測は確率的ですが、キャリブレーションされていません。
  * `predict_mode(mach, Xnew)`: 上記で返された確率的予測のモードを返します。
  * `transform(mach, Xnew)`: `Xnew`が`X`と同じスキーマを持つと仮定して、`MLJFlux.EntityEmbedderLayer`レイヤーを使用して`Xnew`のカテゴリカル特徴を密な`Continuous`ベクトルに変換します。モデルがカテゴリカル特徴を欠く入力`X`でトレーニングされた場合は何もしません。

# フィッティングパラメータ

`fitted_params(mach)`のフィールドは次のとおりです：

  * `chain`: トレーニングされた「チェーン」（Flux.jlモデル）、すなわちニューラルネットワークを構成するレイヤー、関数、および活性化の系列。これには、`finaliser`で指定された最終レイヤー（例：`softmax`）が含まれます。

# レポート

`report(mach)`のフィールドは次のとおりです：

  * `training_losses`: 履歴順に並んだトレーニング損失のベクトル（`lambda != 0`の場合はペナルティ付き）、長さは`epochs + 1`です。最初の要素はトレーニング前の損失です。

# 例

この例では、Irisデータセットを使用して分類モデルを構築します。これは非常に基本的な例で、デフォルトのビルダーを使用し、標準化は行いません。より高度な例については、[`NeuralNetworkRegressor`](@ref)や[`ImageClassifier`](@ref)、およびMLJFlux.jlのドキュメント内の例を参照してください。

```julia
using MLJ, Flux
import Optimisers
import RDatasets
```

まず、データをロードします。

```julia
mtcars = RDatasets.dataset("datasets", "mtcars");
y, X = unpack(mtcars, ==(:VS), in([:MPG, :Cyl, :Disp, :HP, :WT, :QSec]));
```

`y`はベクトルで、`X`はテーブルであることに注意してください。

```julia
y = categorical(y) # 分類器はカテゴリカル入力を受け取ります
X_f32 = Float32.(X) # ニューラルネットワークレイヤーの浮動小数点型に合わせる
NeuralNetworkBinaryClassifier = @load NeuralNetworkBinaryClassifier pkg=MLJFlux
bclf = NeuralNetworkBinaryClassifier()
```

次に、モデルをトレーニングします。

```julia
mach = machine(bclf, X_f32, y)
fit!(mach)
```

`optimizer_changes_trigger_retraining`が`false`（デフォルト）であれば、学習率を変更しながらインクリメンタルにモデルをトレーニングできます。ここでは、（合計）イテレーション数も変更します。

```julia-repl
julia> bclf.optimiser
Adam(0.001, (0.9, 0.999), 1.0e-8)
```

```julia
bclf.optimiser = Optimisers.Adam(eta = bclf.optimiser.eta * 2)
bclf.epochs = bclf.epochs + 5

fit!(mach, verbosity=2) # さらに5エポックトレーニングします
```

`cross_entropy`関数を使用して平均トレーニング損失を確認できます。

```julia
training_loss = cross_entropy(predict(mach, X_f32), y)
```

`fitted_params`を使用してFluxチェーン（モデル）にアクセスできます。

```julia
chain = fitted_params(mach).chain
```

最後に、MLJの`learning_curve`関数を使用して、サンプル外のパフォーマンスが時間とともにどのように変化するかを確認できます。

```julia
r = range(bclf, :epochs, lower=1, upper=200, scale=:log10)
curve = learning_curve(
    bclf,
    X_f32,
    y,
    range=r,
    resampling=Holdout(fraction_train=0.7),
    measure=cross_entropy,
)
using Plots
plot(
   curve.parameter_values,
   curve.measurements,
   xlab=curve.parameter_name,
   xscale=curve.parameter_scale,
   ylab = "Cross Entropy",
)

```

さらに[`ImageClassifier`](@ref)も参照してください。
