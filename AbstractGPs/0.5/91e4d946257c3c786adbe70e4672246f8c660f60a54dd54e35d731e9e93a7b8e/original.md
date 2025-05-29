```
var(f::FiniteGP)
```

Compute only the diagonal elements of [`cov(f)`](@ref).

# Examples

```jldoctest
julia> fx = GP(Matern52Kernel())(randn(10), 0.1);

julia> var(fx) == diag(cov(fx))
true
```
