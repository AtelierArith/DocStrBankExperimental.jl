```
univariate_maximize(f, a::Real, b::Real, transform, optimizer::GoldenSectionOpt, tol::Real)
```

Maximizes `f(x)` using a Golden Section Search. See `?golden_section_maximize`.

# Examples

```jldoctest
julia> f(x) = -(x-2)^2
f (generic function with 1 method)

julia> m = univariate_maximize(f, 1, 5, identity, GoldenSectionOpt(), 1e-10)
2.0000000000051843
```
