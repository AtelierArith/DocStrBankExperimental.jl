```
MultitargetNeuralNetworkRegressor
```

マルチターゲットニューラルネットワーク回帰器を構築するためのモデルタイプで、[MLJFlux.jl](https://github.com/alan-turing-institute/MLJFlux.jl)に基づき、MLJモデルインターフェースを実装しています。

MLJからは、次のようにしてタイプをインポートできます。

```
MultitargetNeuralNetworkRegressor = @load MultitargetNeuralNetworkRegressor pkg=MLJFlux
```

`model = MultitargetNeuralNetworkRegressor()`を実行して、デフォルトのハイパーパラメータでインスタンスを構築します。ハイパーパラメータのデフォルトを上書きするには、`MultitargetNeuralNetworkRegressor(builder=...)`のようにキーワード引数を提供します。

`MultitargetNeuralNetworkRegressor`は、`Continuous`ターゲットの多値を予測するためにデータ依存のFlux.jlニューラルネットワークをトレーニングするためのもので、`Continuous`特徴のテーブルが与えられた場合に使用されます。ユーザーは、遭遇したデータの特性に基づいてネットワークを構築するためのレシピを提供し、適切な`builder`を指定します。ビルダーに関する詳細はMLJFluxのドキュメントを参照してください。

`Continuous`科学要素タイプの特徴に加えて、このモデルは入力テーブル内のカテゴリカル特徴もサポートしています。存在する場合、そのような特徴は、入力の後に追加の`EntityEmbedderLayer`レイヤーを使用して密なベクトルに埋め込まれます。これは、Cheng Guo、Felix Berkhahnによる「Categorical Variablesのエンティティ埋め込み」に記載されています。

# トレーニングデータ

MLJまたはMLJBaseでは、次のようにしてデータにインスタンス`model`をバインドします。

```
mach = machine(model, X, y)
```

ここで：

  * `X`は入力特徴を提供し、次のいずれかです：(i) `Continuous`要素のscitypeを持つ`Matrix`（通常は`Float32`）; または (ii) `Continuous`、`Multiclass`、または`OrderedFactor`要素のscitypeを持つ入力特徴のテーブル（例：`DataFrame`）; 列のscitypesは`schema(X)`で確認できます。`Multiclass`または`OrderedFactor`特徴が存在する場合、構築されたネットワークはそれらを密なベクトルに変換するために`EntityEmbedderLayer`レイヤーを使用します。`X`が`Matrix`の場合、列は特徴に対応し、行は観測に対応していると見なされます。
  * `y`はターゲットで、要素のscitypeが`Continuous`である任意のテーブルまたは行列の出力ターゲットです; 列のscitypesは`schema(y)`で確認できます。`y`が`Matrix`の場合、変数に対応する列と観測に対応する行を持つと見なされます。

# ハイパーパラメータ

  * `builder=MLJFlux.Linear(σ=Flux.relu)`: ニューラルネットワークを構築するMLJFluxビルダー。可能な`builders`には、`Linear`、`Short`、および`MLP`が含まれます。ビルダーに関する詳細はMLJFluxのドキュメントを参照し、以下の例で`@builder`便利マクロの使用を確認してください。
  * `optimiser::Optimisers.Adam()`: Optimisers.jlオプティマイザー。オプティマイザーはネットワークの重みの更新を行います。学習率（オプティマイザーの更新率）を選択するための良いルールは、`10e-3`から始め、`1`と`1e-7`の間の`10`の累乗を使用して調整することです。
  * `loss=Flux.mse`: ネットワークが最適化する損失関数。`loss(yhat, y)`の形式で呼び出すことができる関数である必要があります。可能な損失関数は[Fluxの損失関数のドキュメント](https://fluxml.ai/Flux.jl/stable/models/losses/)にリストされています。回帰タスクの場合、自然な損失関数は次のとおりです：

      * `Flux.mse`
      * `Flux.mae`
      * `Flux.msle`
      * `Flux.huber_loss`

    現在、MLJの測定値はここで損失関数としてサポートされていません。
  * `epochs::Int=10`: エポックでのトレーニングの期間。通常、1エポックはトレーニングデータセット全体を1回通過することを表します。
  * `batch_size::int=1`: トレーニングに使用されるバッチサイズで、ネットワークの重みの更新ごとのサンプル数を表します。通常、バッチサイズは`8`から`512`の間です。バッチサイズを増やすと、`acceleration=CUDALibs()`でGPUが利用可能な場合、トレーニングが加速される可能性があります。
  * `lambda::Float64=0`: 重みの正則化ペナルティの強さ。範囲`[0, ∞)`の任意の値を取ることができます。履歴はペナルティなしの損失を報告します。
  * `alpha::Float64=0`: 正則化のL2/L1ミックスで、範囲`[0, 1]`の値です。0の値はL2正則化を表し、1の値はL1正則化を表します。
  * `rng::Union{AbstractRNG, Int64}`: トレーニング中に使用される乱数生成器またはシード。デフォルトは`Random.default_rng()`です。
  * `optimizer_changes_trigger_retraining::Bool=false`: 関連するオプティマイザーが変更された場合にマシンを再フィッティングするときに何が起こるかを定義します。`true`の場合、関連するマシンは`fit!`呼び出し時に最初から再トレーニングされます。そうでない場合は、再トレーニングされません。
  * `acceleration::AbstractResource=CPU1()`: トレーニングが行われるハードウェアを定義します。GPUでのトレーニングには`CUDALibs()`を使用します。
  * `embedding_dims`: カテゴリカル特徴の名前をシンボルとしてキーに持ち、そのような特徴のエンティティ埋め込みの希望する次元数を表す数値を値に持つ`Dict`です。整数値の`7`は埋め込みの次元数を`7`に設定し、浮動小数点値の`0.5`は埋め込みの次元数を`ceil(0.5 * c)`に設定します。ここで、`c`は特徴レベルの数です。指定されていない特徴の次元数は`min(c - 1, 10)`にデフォルト設定されます。

# 操作

  * `predict(mach, Xnew)`: 新しい特徴`Xnew`が上記の`X`と同じscitypeを持つ場合、ターゲットの予測を返します。予測は決定論的です。
  * `transform(mach, Xnew)`: `Xnew`が`X`と同じスキーマを持つと仮定し、ネットワーク内の`MLJFlux.EntityEmbedderLayer`レイヤーを使用して`Xnew`のカテゴリカル特徴を密な`Continuous`ベクトルに変換します。モデルがカテゴリカル特徴を欠く入力`X`でトレーニングされた場合は何もしません。

# フィッティングパラメータ

`fitted_params(mach)`のフィールドは次のとおりです：

  * `chain`: トレーニングされた「チェーン」（Flux.jlモデル）、すなわちニューラルネットワークを構成するレイヤー、関数、および活性化の系列。

# レポート

`report(mach)`のフィールドは次のとおりです：

  * `training_losses`: 歴史的順序でのトレーニング損失のベクトル（`lambda != 0`の場合はペナルティ付き）、長さは`epochs + 1`です。最初の要素はトレーニング前の損失です。

# 例

この例では、合成データにマルチターゲット回帰モデルを適用します：

```julia
using MLJ
import MLJFlux
using Flux
import Optimisers
```

まず、いくつかの合成データを生成します（MLJBase 0.20.16以上が必要です）：

```julia
X, y = make_regression(100, 9; n_targets = 2) # 両方ともテーブル
schema(y)
schema(X)
```

テストセットを分割します：

```julia
(X, Xtest), (y, ytest) = partition((X, y), 0.7, multi=true);
```

次に、便利なマクロを利用して`builder`を定義できます。次の`@builder`呼び出しでは、`n_in`は入力特徴の数のプロキシで、`n_out`はターゲット変数の数（両方とも`fit!`時に知られています）、`rng`はRNGのプロキシです（これは下で定義された`model`の`rng`フィールドから渡されます）。

```julia
builder = MLJFlux.@builder begin
    init=Flux.glorot_uniform(rng)
    Chain(
        Dense(n_in, 64, relu, init=init),
        Dense(64, 32, relu, init=init),
        Dense(32, n_out, init=init),
    )
end
```

回帰モデルをインスタンス化します：

```julia
MultitargetNeuralNetworkRegressor = @load MultitargetNeuralNetworkRegressor
model = MultitargetNeuralNetworkRegressor(builder=builder, rng=123, epochs=20)
```

ターゲットの標準化を行うために、`TransformedTargetModel`でモデルをラップし、特徴の標準化を行うためにラップされたモデルをパイプラインに挿入します：

```julia
pipe = Standardizer |> TransformedTargetModel(model, transformer=Standardizer)
```

高い冗長性（>1）でフィットすると、トレーニング中の損失が表示されます。`report(mach)`の出力でも損失を確認できます。

```julia
mach = machine(pipe, X, y)
fit!(mach, verbosity=2)

# 最初の要素は初期損失、2:endはエポックごとのトレーニング損失
report(mach).transformed_target_model_deterministic.model.training_losses
```

学習率を調整する実験については、[`NeuralNetworkRegressor`](@ref)の例を参照してください。

```
pipe.transformed_target_model_deterministic.model.optimiser = Optimisers.Adam(0.0001)
```

学習率が固定されたので、次にCV推定を計算し（`mach`にバインドされたすべてのデータを使用）、テストセットでのパフォーマンスと比較します：

```julia

# CV推定、`(X, y)`に基づく：
evaluate!(mach, resampling=CV(nfolds=5), measure=multitarget_l2)

# `(Xtest, test)`の損失：
fit!(mach) # すべてのデータ`(X, y)`でトレーニング
yhat = predict(mach, Xtest)
multitarget_l2(yhat, ytest)
```

[`NeuralNetworkRegressor`](@ref)も参照してください。
