```
BoundedMinkowskiCost(μ₁, μ₂)
```

Return value similar to [`MinkowskiCost`](@ref), but ensure costs smaller than 2τ.

### Optional Arguments

`p=1`: the p value for p-norm calculation. `τ=1`: value specifying half of the upper limit of the Minkowski cost.
