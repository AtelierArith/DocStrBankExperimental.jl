```
Hierarchical(nclusters::Int; distance::Function = absolute_distance, linkage::Symbol = :single)
```

バッファカットは、与えられた`linkage`を使用して、一般化された`distance`行列上で、ヒエラルヒカルアルゴリズムを用いて`nclusters`クラスタにソートされます。

以下の距離測定が利用可能です

  * [`absolute_distance`](@ref)
  * [`angular_distance`](@ref)
  * [`spatioangular_distance`](@ref)
