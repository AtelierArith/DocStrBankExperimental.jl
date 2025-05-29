```
DiscreteVoronoi <: NeutralLandscapeMaker

DiscreteVoronoi(; n=3) 
DiscreteVoronoi(n)
```

このタイプは、Voronoiのような図のラスタライズを提供します。`n`個の初期クラスタを使用して、1-NNアルゴリズムを使用して各パッチに値を割り当てます。これは、近傍数`k`が1に設定された`NearestNeighborElement`アルゴリズムです。デフォルトは3つのクラスタを使用します。
