```
KNNDetector(k=5,
            metric=Euclidean,
            algorithm=:kdtree,
            leafsize=10,
            reorder=true,
            reduction=:maximum)
```

インスタンスの異常スコアを、そのk近傍の距離に基づいて計算します。

## パラメータ

```
k::Integer
```

近傍の数（0より大きくなければなりません）。

```
metric::Metric
```

これは、Distances.jlパッケージで定義されたMetricタイプの1つです。Metricのサブタイプとして新しいタイプを作成することで、自分自身のメトリックを定義することが可能です。

```
algorithm::Symbol
```

`(:kdtree, :balltree)`のいずれかです。`kdtree`では、点がハイパープレーンを使用して再帰的にグループに分割されます。したがって、KDTreeは、ユークリッド、チェビシェフ、ミンコフスキー、およびシティブロックのような軸に整列したメトリックでのみ機能します。*brutetree*は、すべての点をブルートフォース方式で線形検索し、任意のメトリックで機能します。*balltree*は、点をハイパー球で制約されたグループに再帰的に分割し、任意のメトリックで機能します。

```
static::Union{Bool, Symbol}
```

`(true, false, :auto)`のいずれかです。フィッティングと変換のための入力データが静的にまたは動的に割り当てられるべきかどうか。`true`の場合、データは静的に割り当てられます。`false`の場合、データは動的に割り当てられます。`:auto`の場合、最後の次元を除くすべての次元の積が100を超える場合、データは動的に割り当てられます。

```
leafsize::Int
```

ツリーをさらに分割するのを停止する点の数を決定します。ツリーをトラバースすることと、増加する点の数に対してメトリック関数を評価する必要があることとの間にはトレードオフがあります。

```
reorder::Bool
```

ツリーを構築する際、距離が近い点をメモリ内で近くに配置します。これはキャッシュの局所性に役立ちます。この場合、元のデータのコピーが作成され、元のデータは変更されません。これはパフォーマンスに大きな影響を与える可能性があり、デフォルトではtrueに設定されています。

```
parallel::Bool
```

利用可能なすべてのスレッドを使用して`score`と`predict`を並列化します。スレッドの数は`JULIA_NUM_THREADS`環境変数で設定できます。注意：`fit`は並列ではありません。

```
reduction::Symbol
```

`(:maximum, :median, :mean)`のいずれかです。(`reduction=:maximum`)は[1]によって提案されました。Angiulliら[2]は距離を減少させるために合計を提案しましたが、数値的安定性のために平均が実装されています。

## 例

```julia
using OutlierDetection: KNNDetector, fit, transform
detector = KNNDetector()
X = rand(10, 100)
model, result = fit(detector, X; verbosity=0)
test_scores = transform(detector, model, X)
```

## 参考文献

[1] Ramaswamy, Sridhar; Rastogi, Rajeev; Shim, Kyuseok (2000): 大規模データセットからの外れ値をマイニングするための効率的なアルゴリズム。

[2] Angiulli, Fabrizio; Pizzuti, Clara (2002): 高次元空間における高速外れ値検出。
