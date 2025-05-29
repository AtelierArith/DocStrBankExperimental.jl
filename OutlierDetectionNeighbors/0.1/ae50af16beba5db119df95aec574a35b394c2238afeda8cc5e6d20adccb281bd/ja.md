```
ABODDetector(k = 5,
             metric = Euclidean(),
             algorithm = :kdtree,
             static = :auto,
             leafsize = 10,
             reorder = true,
             parallel = false,
             enhanced = false)
```

最近傍の角度に基づいて外れ値を特定します。これは、全体のデータセットではなく、最近傍の角度の分散を使用する論文で説明されている`FastABOD`バリアントを実装しています。[1]を参照してください。

*注意:* スコアは反転されており、高いスコアが高い外れ値性を示すという私たちの概念に従っています。

## パラメータ

```
k::Integer
```

近傍の数（0より大きくなければなりません）。

```
metric::Metric
```

これは、Distances.jlパッケージで定義されたMetricタイプの1つです。新しいタイプを作成して独自のメトリックを定義することも可能です。これらはMetricのサブタイプです。

```
algorithm::Symbol
```

`(:kdtree, :balltree)`のいずれかです。`kdtree`では、点がハイパープレーンを使用して再帰的にグループに分割されます。したがって、KDTreeは、ユークリッド、チェビシェフ、ミンコフスキー、シティブロックのような軸に整列したメトリックでのみ機能します。*brutetree*は、すべての点をブルートフォース方式で線形検索し、任意のメトリックで機能します。*balltree*は、点をハイパー球で制約されたグループに再帰的に分割し、任意のメトリックで機能します。

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

すべての利用可能なスレッドを使用して`score`と`predict`を並列化します。スレッドの数は`JULIA_NUM_THREADS`環境変数で設定できます。注意: `fit`は並列ではありません。

```
enhanced::Bool
```

`enhanced=true`の場合、[2]で提案された強化ABOD（EABOD）適応を使用します。

## 例

```julia
using OutlierDetection: ABODDetector, fit, transform
detector = ABODDetector()
X = rand(10, 100)
model, result = fit(detector, X; verbosity=0)
test_scores = transform(detector, model, X)
```

## 参考文献

[1] Kriegel, Hans-Peter; S hubert, Matthias; Zimek, Arthur (2008): 高次元データにおける角度ベースの外れ値検出。

[2] Li, Xiaojie; Lv, Jian Cheng; Cheng, Dongdong (2015): より安定した関係を持つ角度ベースの外れ値検出アルゴリズム。
