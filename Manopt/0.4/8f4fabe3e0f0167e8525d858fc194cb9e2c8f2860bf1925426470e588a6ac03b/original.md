```
X = get_subtrahend_gradient(amp, q)
get_subtrahend_gradient!(amp, X, q)
```

Evaluate the (sub)gradient of the subtrahend `h` from within a [`ManifoldDifferenceOfConvexObjective`](@ref) `amp` at the point `q` (in place of `X`).

The evaluation is done in place of `X` for the `!`-variant. The `T=`[`AllocatingEvaluation`](@ref) problem might still allocate memory within. When the non-mutating variant is called with a `T=`[`InplaceEvaluation`](@ref) memory for the result is allocated.
