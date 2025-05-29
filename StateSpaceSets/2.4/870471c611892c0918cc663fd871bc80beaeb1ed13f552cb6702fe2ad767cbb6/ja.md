```
Hausdorff(metric = Euclidean())
```

[`set_distance`](@ref)で使用できる距離です。[ハウスドルフ距離](https://en.wikipedia.org/wiki/Hausdorff_distance)は、一方の集合の点から他方の集合の最も近い点までのすべての距離の中で最大のものです。この距離は、デフォルトでユークリッド距離となる`Hausdorff`に与えられたメトリックを使用して計算されます。

`Hausdorff`は[`StrictlyMinimumDistance`](@ref)よりも2倍遅いですが、状態空間集合の集合の空間において適切なメトリックです。

このメトリックは、要素が`SVector`である`StateSpaceSet`にのみ適用されます。

開発者向け：`set_distance`は、最初と2番目の集合のKDTreesであるキーワード`tree1, tree2`を受け取ることができます。
