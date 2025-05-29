```
NearestNeighborElement <: NeutralLandscapeMaker

NearestNeighborElement(; n=3, k=1)
NearestNeighborElement(n, [k=1])
```

k-NNアルゴリズムを使用して各パッチに値を割り当てます。`n`は初期クラスタの数、`k`は近傍の数です。デフォルトでは、3つのクラスタと1つの近傍を使用します。
