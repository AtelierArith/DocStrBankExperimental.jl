```
DefiniteIntegral([sp::Space])
```

Return the operator that integrates a `Fun` over its domain. If `sp` is unspecified, it is inferred at runtime from the context.

# Examples

```jldoctest
julia> f = Fun(x -> 3x^2, Chebyshev());

julia> DefiniteIntegral() * f ≈ 2 # integral of 3x^2 over -1..1
true
```
