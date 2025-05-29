```
(s::Space)(n::Integer)
```

Return a `Fun` with the coefficients being a sparse representation of `[zeros(n); 1]`. The result is primarily meant to be evaluated at a specific point.

For orthogonal polynomial spaces, the result will usually represent the `n`-th basis function.

# Examples

```jldoctest
julia> Chebyshev()(2) == Fun(Chebyshev(), [0, 0, 1])
true
```
