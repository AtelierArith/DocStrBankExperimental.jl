```
effective_variables(p::AbstractPolynomialLike)
```

Return a vector of `eltype` `variable_union_type(p)` (see [`variable_union_type`](@ref)), containing all the variables that has nonzero degree in at least one term. That is, return all the variables `v` such that `maxdegree(p, v)` is not zero. The returned vector is sorted in decreasing order.
