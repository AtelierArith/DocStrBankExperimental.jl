```
NeuralNetworkRegressor
```

ニューラルネットワーク回帰器を構築するためのモデルタイプで、[MLJFlux.jl](https://github.com/alan-turing-institute/MLJFlux.jl)に基づいており、MLJモデルインターフェースを実装しています。

MLJからは、次のようにしてタイプをインポートできます。

```
NeuralNetworkRegressor = @load NeuralNetworkRegressor pkg=MLJFlux
```

`model = NeuralNetworkRegressor()`を実行して、デフォルトのハイパーパラメータでインスタンスを構築します。ハイパーパラメータのデフォルトをオーバーライドするには、`NeuralNetworkRegressor(builder=...)`のようにキーワード引数を提供します。

`NeuralNetworkRegressor`は、`Continuous`ターゲットを予測するためにデータ依存のFlux.jlニューラルネットワークをトレーニングするためのもので、`Continuous`特徴のテーブルが与えられます。ユーザーは、遭遇したデータの特性に基づいてネットワークを構築するためのレシピを提供し、適切な`builder`を指定します。ビルダーに関する詳細はMLJFluxのドキュメントを参照してください。

`Continuous`科学要素タイプの特徴に加えて、このモデルは入力テーブル内のカテゴリカル特徴もサポートしています。存在する場合、そのような特徴は、入力の後に追加の`EntityEmbedderLayer`レイヤーを使用して密なベクトルに埋め込まれます。これは、Cheng Guo、Felix Berkhahnによる「Categorical Variablesのエンティティ埋め込み」に記載されています。

# トレーニングデータ

MLJまたはMLJBaseでは、次のようにしてデータにインスタンス`model`をバインドします。

```
mach = machine(model, X, y)
```

ここで：

  * `X`は入力特徴を提供し、次のいずれかです：(i) `Continuous`要素のscitypeを持つ`Matrix`（通常は`Float32`）；または(ii) `Continuous`、`Multiclass`、または`OrderedFactor`要素のscitypeを持つ入力特徴のテーブル（例：`DataFrame`）；列のscitypeは`schema(X)`で確認できます。`Multiclass`または`OrderedFactor`特徴が存在する場合、構築されたネットワークはそれらを密なベクトルに変換するために`EntityEmbedderLayer`レイヤーを使用します。`X`が`Matrix`の場合、列は特徴に対応し、行は観測に対応していると見なされます。
  * `y`はターゲットで、要素のscitypeが`Continuous`である任意の`AbstractVector`であることができます；scitypeは`scitype(y)`で確認できます。

`fit!(mach, rows=...)`を使用してマシンをトレーニングします。

# ハイパーパラメータ

  * `builder=MLJFlux.Linear(σ=Flux.relu)`：ニューラルネットワークを構築するMLJFluxビルダー。可能な`builders`には、`MLJFlux.Linear`、`MLJFlux.Short`、および`MLJFlux.MLP`が含まれます。ビルダーに関する詳細はMLJFluxのドキュメントを参照し、以下の例で`@builder`便利マクロの使用を確認してください。
  * `optimiser::Optimisers.Adam()`：Optimisers.jlオプティマイザー。オプティマイザーはネットワークの重みの更新を行います。学習率（オプティマイザーの更新率）を選択するための良い目安は、`10e-3`から始め、`1`と`1e-7`の間の`10`の累乗を使用して調整することです。
  * `loss=Flux.mse`：ネットワークが最適化する損失関数。`loss(yhat, y)`の形式で呼び出すことができる関数である必要があります。可能な損失関数は[Flux損失関数のドキュメント](https://fluxml.ai/Flux.jl/stable/models/losses/)にリストされています。回帰タスクにおける自然な損失関数は：

      * `Flux.mse`
      * `Flux.mae`
      * `Flux.msle`
      * `Flux.huber_loss`

    現在、MLJの測定値はここで損失関数としてサポートされていません。
  * `epochs::Int=10`：エポックでのトレーニングの期間。通常、1エポックはトレーニングデータセット全体を1回通過することを表します。
  * `batch_size::int=1`：トレーニングに使用されるバッチサイズで、ネットワークの重みの更新ごとのサンプル数を表します。通常、バッチサイズは`8`から`512`の間です。バッチサイズを増やすと、`acceleration=CUDALibs()`でGPUが利用可能な場合、トレーニングが加速される可能性があります。
  * `lambda::Float64=0`：重みの正則化ペナルティの強さ。範囲は`[0, ∞)`の任意の値を取ることができます。履歴はペナルティなしの損失を報告します。
  * `alpha::Float64=0`：正則化のL2/L1ミックスで、範囲は`[0, 1]`です。値が0の場合はL2正則化を表し、値が1の場合はL1正則化を表します。
  * `rng::Union{AbstractRNG, Int64}`：トレーニング中に使用される乱数生成器またはシード。デフォルトは`Random.default_rng()`です。
  * `optimizer_changes_trigger_retraining::Bool=false`：関連するオプティマイザーが変更された場合にマシンを再フィッティングするときに何が起こるかを定義します。`true`の場合、関連するマシンは`fit!`呼び出し時に最初から再トレーニングされます。それ以外の場合は再トレーニングされません。
  * `acceleration::AbstractResource=CPU1()`：トレーニングが行われるハードウェアを定義します。GPUでのトレーニングには`CUDALibs()`を使用します。
  * `embedding_dims`：カテゴリカル特徴の名前をシンボルとしてキーに持ち、そのような特徴のエンティティ埋め込みの望ましい次元数を表す数値を値に持つ`Dict`です：整数値`7`は埋め込みの次元数を`7`に設定し、浮動小数点値`0.5`は埋め込みの次元数を`ceil(0.5 * c)`に設定します。ここで、`c`は特徴レベルの数です。指定されていない特徴の次元数は`min(c - 1, 10)`にデフォルト設定されます。

# 操作

  * `predict(mach, Xnew)`：新しい特徴`Xnew`が与えられたときのターゲットの予測を返します。`X`と同じscitypeを持つ必要があります。
  * `transform(mach, Xnew)`：`Xnew`が`X`と同じスキーマを持つと仮定し、ネットワーク内の`MLJFlux.EntityEmbedderLayer`レイヤーを使用して`Xnew`のカテゴリカル特徴を密な`Continuous`ベクトルに変換します。モデルがカテゴリカル特徴を欠く入力`X`でトレーニングされた場合は何もしません。

# フィッティングされたパラメータ

`fitted_params(mach)`のフィールドは次のとおりです：

  * `chain`：トレーニングされた「チェーン」（Flux.jlモデル）、すなわちニューラルネットワークを構成するレイヤー、関数、および活性化の系列。

# レポート

`report(mach)`のフィールドは次のとおりです：

  * `training_losses`：歴史的順序でのトレーニング損失のベクトル（`lambda != 0`の場合はペナルティ付き）、長さは`epochs + 1`です。最初の要素はトレーニング前の損失です。

# 例

この例では、ボストンの住宅価格データセットの回帰モデルを構築します。

```julia
using MLJ
import MLJFlux
using Flux
import Optimisers
```

まず、データを読み込みます：`:MEDV`列はターゲットベクトル`y`になり、残りのすべての列はテーブル`X`に入りますが、`:CHAS`は除外されます。

```julia
data = OpenML.load(531); # Loads from https://www.openml.org/d/531
y, X = unpack(data, ==(:MEDV), !=(:CHAS); rng=123);

scitype(y)
schema(X)
```

MLJFluxモデルは順序付き因子を処理しないため、`:RAD`を`Continuous`として扱います。

```julia
X = coerce(X, :RAD=>Continuous)
```

テストセットを分割します：

```julia
(X, Xtest), (y, ytest) = partition((X, y), 0.7, multi=true);
```

次に、便利なマクロを使用して`builder`を定義できます。次の`@builder`呼び出しでは、`n_in`は入力特徴の数のプロキシ（`fit!`時に知られることになります）であり、`rng`はモデルの`rng`フィールドから渡されるRNGのプロキシです。また、出力特徴の数を表すパラメータ`n_out`もあります。単一ターゲット回帰を行っているため、渡される値は常に`1`ですが、定義するビルダーは[`MultitargetNeuralNetworkRegressor`](@ref)にも適用されます。

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

モデルをインスタンス化します：

```julia
NeuralNetworkRegressor = @load NeuralNetworkRegressor pkg=MLJFlux
model = NeuralNetworkRegressor(
    builder=builder,
    rng=123,
    epochs=20
)
```

ターゲットの標準化を行うためにモデルを`TransformedTargetModel`でラップし、特徴の標準化を行うためにラップされたモデルをパイプラインに挿入します：

```julia
pipe = Standardizer |> TransformedTargetModel(model, transformer=Standardizer)
```

高い冗長性（>1）でフィットさせると、トレーニング中の損失が表示されます。`report(mach)`の出力でも損失を見ることができます。

```julia
mach = machine(pipe, X, y)
fit!(mach, verbosity=2)

# first element initial loss, 2:end per epoch training losses
report(mach).transformed_target_model_deterministic.model.training_losses
```

## 学習率の実験

学習率が予測にどのように影響するかを視覚的に比較できます：

```julia
using Plots

rates = rates = [5e-5, 1e-4, 0.005, 0.001, 0.05]
plt=plot()

foreach(rates) do η
  pipe.transformed_target_model_deterministic.model.optimiser = Optimisers.Adam(η)
  fit!(mach, force=true, verbosity=0)
  losses =
      report(mach).transformed_target_model_deterministic.model.training_losses[3:end]
  plot!(1:length(losses), losses, label=η)
end

plt

pipe.transformed_target_model_deterministic.model.optimiser.eta = Optimisers.Adam(0.0001)
```

学習率を固定した状態で、パフォーマンスのCV推定を計算し（`mach`にバインドされたすべてのデータを使用）、これをテストセットのパフォーマンスと比較します：

```julia
# CV estimate, based on `(X, y)`:
evaluate!(mach, resampling=CV(nfolds=5), measure=l2)

# loss for `(Xtest, test)`:
fit!(mach) # train on `(X, y)`
yhat = predict(mach, Xtest)
l2(yhat, ytest)
```

これらの損失は、パイプラインモデルに対して、元の標準化されていないスケールのターゲットを指します。

停止基準や他の反復制御を実装するには、MLJFluxのドキュメントからリンクされた例を参照してください。

[`MultitargetNeuralNetworkRegressor`](@ref)も参照してください。
