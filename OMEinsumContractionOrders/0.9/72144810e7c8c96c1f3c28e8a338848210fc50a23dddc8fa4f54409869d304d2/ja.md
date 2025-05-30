```
KaHyParBipartite{RT,IT,GM}
KaHyParBipartite(; sc_target, imbalances=collect(0.0:0.005:0.8),
    max_group_size=40, greedy_config=GreedyMethod())
```

KaHyPar + Greedyアプローチを使用してeinsumコードの収束順序を最適化します。このプログラムは、最初にKaHyParを使用してテンソルをいくつかのグループに再帰的に分割し、`max_group_size`で指定された最大グループサイズと`sc_target`で指定された最大空間複雑性を持ちます。その後、貪欲探索アルゴリズムを使用して各グループ内の収束順序を見つけます。他の引数は次のとおりです。

  * `sc_target`は、最大テンソルの要素数の対数として定義されるターゲット空間複雑性です。
  * `imbalances`は、階層的二分割におけるグループサイズを制御するKaHyParのパラメータです。
  * `max_group_size`は、貪欲探索に使用できる最大サイズです。
  * `greedy_config`は、貪欲最適化器です。

### 参考文献

  * [ハイパー最適化されたテンソルネットワーク収束](https://arxiv.org/abs/2002.01935)
  * [Sycamore量子優越性回路のシミュレーション](https://arxiv.org/abs/2103.03074)
