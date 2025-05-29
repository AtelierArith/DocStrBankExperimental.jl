```
set_distance(ssset1, ssset2 [, distance])
```

2つの`StateSpaceSet`間の距離を計算します。すなわち、`distance`によって定義された点の集合間の距離です。

可能な`distance`のタイプは次のとおりです：

  * [`Centroid`](@ref)、これはデフォルトであり、他のものよりも100倍速いです
  * [`Hausdorff`](@ref)
  * [`StrictlyMinimumDistance`](@ref)
  * 2つの状態空間セット`A, B`間の距離を返す任意の関数`f(A, B)`。
