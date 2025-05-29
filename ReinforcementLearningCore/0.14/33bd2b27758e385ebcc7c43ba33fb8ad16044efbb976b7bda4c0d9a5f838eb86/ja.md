```
WeightedExplorer(;is_normalized::Bool, rng=Random.default_rng())
```

`is_normalized` は、与えられたアクション値がすでに合計 `1.0` に正規化されているかどうかを示すために使用されます。

!!! warning
    要素は `>=0` であると仮定されます。


参照: [`WeightedSoftmaxExplorer`](@ref)
