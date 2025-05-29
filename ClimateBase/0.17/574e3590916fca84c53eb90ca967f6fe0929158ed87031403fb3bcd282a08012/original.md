```
missing_weights(A::ClimArray, val = missing_val(A)) → B, W
```

Generate a new array `B` with values like `A`, but with `A`'s `missing` values replaced with `val`. Also generate an array of weights, which has the value 0 when `A` had `missing`, and the value `1` otherwise.

The output of this function should be used in conjunction with any of ClimateBase.jl aggregating functions like `spacemean, timemean, ...`, when your data have `missing` values which you want to *completely skip* during the aggregation process.

This function returns `A, nothing` if `A` has no `missing` values.
