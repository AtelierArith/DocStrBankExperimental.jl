```
prod(strategy, left, right)
```

`prod` function is used to find a product of two probability distributions (or any other objects) over same variable (e.g. 𝓝(x|μ*1, σ*1) × 𝓝(x|μ*2, σ*2)). There are multiple strategies for prod function, e.g. `ClosedProd`, `GenericProd` or `PreserveTypeProd`.

See also: [`default_prod_rule`](@ref), [`ClosedProd`](@ref), [`PreserveTypeProd`](@ref), [`GenericProd`](@ref)
