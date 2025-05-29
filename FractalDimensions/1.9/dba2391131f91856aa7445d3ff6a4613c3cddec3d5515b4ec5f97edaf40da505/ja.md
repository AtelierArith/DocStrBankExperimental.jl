```
minimum_pairwise_distance(X::StateSpaceSet, kdtree = dimension(X) < 10, metric = Euclidean())
```

`min_d, min_pair`を返します：データセット内のすべての点の最小ペア間距離と、対応する点のペア。第三引数はKDTreesを使用するか、ブルートフォース検索を使用するかのスイッチです。
