```
EntityEmbedder(; model=mljflux_neural_model)
```

`EntityEmbedder`は、Cheng Guo、Felix Berkhahnによる「Categorical Variablesのエンティティ埋め込み」論文におけるエンティティ埋め込みを実装しています。

# トレーニングデータ

MLJ（またはMLJBase）で、インスタンスの非監視`model`をデータにバインドするには、

```
mach = machine(model, X, y)
```

ここで：

  * `X`は、ラップされているモデルによってサポートされる任意の入力特徴のテーブルです。変換される特徴は、要素のscitypeが`Multiclass`または`OrderedFactor`である必要があります。`schema(X)`を使用してscitypesを確認してください。
  * `y`はターゲットであり、ラップされているモデルによってサポートされる任意の`AbstractVector`であることができます。

`fit!(mach)`を使用してマシンをトレーニングします。

# ハイパーパラメータ

  * `model`: エンティティ埋め込みに使用される監視付きMLJFluxニューラルネットワークモデル。これは、`MLJFlux.NeuralNetworkClassifier`、`NeuralNetworkBinaryClassifier`、`MLJFlux.NeuralNetworkRegressor`、`MLJFlux.MultitargetNeuralNetworkRegressor`のいずれかである必要があります。選択されたモデルには、埋め込み性能に影響を与える可能性のあるハイパーパラメータがある場合があり、最も注目すべきは`builder`引数です。

# 操作

  * `transform(mach, Xnew)`: トレーニングされた`MLJFlux.EntityEmbedderLayer`レイヤーを使用して、`Xnew`のカテゴリカル特徴を密な`Continuous`ベクトルに変換します。関連するドキュメントは[こちら](https://fluxml.ai/MLJFlux.jl/dev/)を確認し、特に`embedding_dims`ハイパーパラメータを参照してください。

# 例

```julia
using MLJ
using CategoricalArrays

# データのセットアップ
N = 200
X = (;
    Column1 = repeat(Float32[1.0, 2.0, 3.0, 4.0, 5.0], Int(N / 5)),
    Column2 = categorical(repeat(['a', 'b', 'c', 'd', 'e'], Int(N / 5))),
    Column3 = categorical(repeat(["b", "c", "d", "f", "f"], Int(N / 5)), ordered = true),
    Column4 = repeat(Float32[1.0, 2.0, 3.0, 4.0, 5.0], Int(N / 5)),
    Column5 = randn(Float32, N),
    Column6 = categorical(
        repeat(["group1", "group1", "group2", "group2", "group3"], Int(N / 5)),
    ),
)
y = categorical([1, 2, 3, 4, 5, 6, 7, 8, 9, 10])           # 分類

# モデルの初期化
EntityEmbedder = @load EntityEmbedder pkg=MLJFlux
NeuralNetworkClassifier = @load NeuralNetworkClassifier pkg=MLJFlux

clf = NeuralNetworkClassifier(embedding_dims=Dict(:Column2 => 2, :Column3 => 2))

emb = EntityEmbedder(clf)

# マシンの構築
mach = machine(emb, X, y)

# モデルのトレーニング
fit!(mach)

# モデルを使用してデータを変換し、カテゴリカル列をエンコード
Xnew = transform(mach, X)
Xnew
```

[`NeuralNetworkClassifier`, `NeuralNetworkRegressor`](@ref)も参照してください。
