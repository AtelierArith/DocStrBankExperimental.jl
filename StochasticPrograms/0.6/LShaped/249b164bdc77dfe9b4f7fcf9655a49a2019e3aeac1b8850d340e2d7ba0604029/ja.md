```
Kmedoids(nclusters::Int; distance::Function = absolute_distance)
```

バッファカットは、一般化された `distance` 行列に対して K-メドイドアルゴリズムを使用して `nclusters` クラスタにソートされます。

以下の距離測定が利用可能です

  * [`absolute_distance`](@ref)
  * [`angular_distance`](@ref)
  * [`spatioangular_distance`](@ref)
