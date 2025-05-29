```
NearestNeighborCorrespondence <: AbstractCorrespondence
```

各ブロブに対して、ブロブに最も近い測定値を割り当てます。この方法では、同じ測定値を複数のブロブに割り当てることができます。

# パラメータ

  * `dist_th=2`: ブロブと測定値の間で許可される最大マハラノビス距離
