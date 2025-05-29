```
WeightedExplorer(;is_normalized::Bool, rng=Random.default_rng())
```

`is_normalized` is used to indicate if the fed action values are already normalized to have a sum of `1.0`.

!!! warning
    Elements are assumed to be `>=0`.


See also: [`WeightedSoftmaxExplorer`](@ref)
