```
AuroraKNN(;kKNN=1000, loocv=true, tree=KDTree,
           pca=false, pca_dimension=false)
```

`k`-最近傍法を用いたAurora。`looc=false`の場合、`k`は`kKNN`に等しく選ばれますが、`loocv=true`の場合、`k`は1,...,`kKNN`の選択肢の中からLeave-One-Out交差検証によって各保持されたレプリカのために選択されます。

`tree`は最近傍計算戦略を説明します。以下のオプションが利用可能です：`:auto`、および`NearestNeighbors.jl`パッケージからの`:kdtree`、`:balltree`、`:brutetree`。

`pca=true`の場合、PCA（主成分分析）を使用して最近傍を見つけるための次元削減戦略が採用されます。各保持されたレプリカについて、順序統計量は次元`pca_dimension`の主成分部分空間に投影されます。この場合、結果として得られる最近傍は近似的な最近傍としてのみ解釈されることに注意してください。
