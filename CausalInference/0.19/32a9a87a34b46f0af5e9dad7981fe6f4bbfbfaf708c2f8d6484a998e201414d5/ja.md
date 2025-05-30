```
alt_cpdag(g::DiGraph)
```

DAGからCPDAGを計算します。すべてのエッジを順序付けることなく、Chickeringの変換アルゴリズムのより簡単な適応を使用します（`d`-分離を独立性テストとして使用するPCアルゴリズムに相当、`pc_oracle`を参照）。

参考文献: M. Chickering: Bayesianネットワーク構造の同値クラスの学習。Journal of Machine Learning Research 2 (2002)。M. Chickering: 同値なBayesianネットワーク構造の変換的特徴付け。(1995)。
