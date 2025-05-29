```
DNNDetector(d = 0,
            metric = Euclidean(),
            algorithm = :kdtree,
            leafsize = 10,
            reorder = true,
            parallel = false)
```

半径 `d` のハイパー球内の近傍の数に基づく異常スコア。Knorr et al. [1] は、得られた外れ値スコアをラベルに直接変換したため、この実装は論文のアプローチを完全には反映していません。

## パラメータ

```
d::Real
```

インスタンスのグローバル密度を計算するために使用されるハイパー球の半径。

```
metric::Metric
```

これは、Distances.jl パッケージで定義された Metric タイプの1つです。新しいタイプを作成して独自のメトリックを定義することも可能です。

```
algorithm::Symbol
```

`(:kdtree, :balltree)` のいずれか。`kdtree` では、点がハイパープレーンを使用して再帰的にグループに分割されます。したがって、KDTree は、ユークリッド、チェビシェフ、ミンコフスキー、シティブロックのような軸に整列したメトリックでのみ機能します。*brutetree* は、すべての点をブルートフォース方式で線形検索し、任意のメトリックで機能します。*balltree* は、点をハイパー球で制約されたグループに再帰的に分割し、任意のメトリックで機能します。

```
static::Union{Bool, Symbol}
```

`(true, false, :auto)` のいずれか。フィッティングと変換のための入力データが静的にまたは動的に割り当てられるべきかどうか。`true` の場合、データは静的に割り当てられます。`false` の場合、データは動的に割り当てられます。`:auto` の場合、最後の次元を除くすべての次元の積が100を超える場合、データは動的に割り当てられます。

```
leafsize::Int
```

ツリーをさらに分割するのを停止する点の数を決定します。ツリーをトラバースすることと、増加する点の数に対してメトリック関数を評価する必要があることとの間にはトレードオフがあります。

```
reorder::Bool
```

ツリーを構築する際、距離が近い点をメモリ内で近くに配置します。これはキャッシュの局所性に役立ちます。この場合、元のデータのコピーが作成され、元のデータは変更されません。これはパフォーマンスに大きな影響を与える可能性があり、デフォルトでは true に設定されています。

```
parallel::Bool
```

利用可能なすべてのスレッドを使用して `score` と `predict` を並列化します。スレッドの数は `JULIA_NUM_THREADS` 環境変数で設定できます。注意: `fit` は並列ではありません。

## 例

```julia
using OutlierDetection: DNNDetector, fit, transform
detector = DNNDetector()
X = rand(10, 100)
model, result = fit(detector, X; verbosity=0)
test_scores = transform(detector, model, X)
```

## 参考文献

[1] Knorr, Edwin M.; Ng, Raymond T. (1998): Algorithms for Mining Distance-Based Outliers in Large Datasets.
