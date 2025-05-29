```
≈(md1, md2)
isapprox(md1, md2)
```

Determine whether two `AbstractMultiDataset`s are similar, that is,  if they have same variable groupings and variables. Note that this means no check over instances is performed.

If the intent is to check if two `AbstractMultiDataset`s have same instances in the same order use [`isequal`](@ref) instead. If the intent is to check if two `AbstractMultiDataset`s have same instances regardless of the order use [`isapproxeq`](@ref) instead.
