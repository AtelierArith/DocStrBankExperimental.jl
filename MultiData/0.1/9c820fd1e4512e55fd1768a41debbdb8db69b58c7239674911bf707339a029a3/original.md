```
≊(md1, md2)
isapproxeq(md1, md2)
```

Determine whether two `AbstractMultiDataset`s have the same variable groupings, variables and instances.

Note: the order of the instance does not matter.

If the intent is to check if two `AbstractMultiDataset`s have same instances in the same order use [`isequal`](@ref) instead. If the intent is to check if two `AbstractMultiDataset`s have same variable groupings and variables use [`isapprox`](@ref) instead.

TODO review
