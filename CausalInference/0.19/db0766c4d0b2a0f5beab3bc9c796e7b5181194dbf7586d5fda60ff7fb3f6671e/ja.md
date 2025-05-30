```
cpdag(skel::DiGraph)
```

DAGからCPDAGを計算します。これはChickeringの変換アルゴリズムを使用しており、`d`-分離を独立性テストとして用いるPCアルゴリズムと同等です（`pc_oracle`を参照）。

参考文献: M. Chickering: Bayesianネットワーク構造の同値クラスの学習。Journal of Machine Learning Research 2 (2002). M. Chickering: 同値のベイジアンネットワーク構造の変換的特徴付け。(1995)。

ここで定義されるエッジの順序は、すでにDiGraphの表現に部分的にエンコードされています。
