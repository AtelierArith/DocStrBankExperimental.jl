```
knn(Xtrain, Xtest, k, batch_size; metric, convert, algorithm)
```

複数の点の最近傍を決定するためのすべての並列実装へのインターフェースであり、`Xtrain`および`Xtest`の各列は点に対応します。

## パラメータ

```
Xtrain::M where M <: AbstractMatrix{<:AbstractFloat}
```

トレーニングポイントの行列。

```
Xtest::M where M <: AbstractMatrix{<:AbstractFloat}
```

テストポイントの行列。

```
k::Int
```

トレーニングポイントで見つける最近傍の数。

```
batch_size::Int
```

トレーニングおよび/またはテストデータを分割するためのバッチサイズ。

```
metric::PreMetric
```

距離計算に使用する（前）メトリック。

```
convert::Function
```

入力データ（`Xtrain`および`Xtest`）を適切な形式に変換するための変換関数、例：`CUDA.cu`。

```
algorithm::Symbol
```

最近傍を決定するために使用する特定のアルゴリズム。
