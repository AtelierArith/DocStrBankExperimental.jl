```
Fun(f)
```

Return `Fun(f, space)` by choosing an appropriate `space` for the function. For univariate functions, `space` is chosen to be `Chebyshev()`, whereas for multivariate functions, it is a tensor product of `Chebyshev()` spaces.

# Examples

```jldoctest
julia> f = Fun(x -> x^2)
Fun(Chebyshev(), [0.5, 0.0, 0.5])

julia> f(0.1) == (0.1)^2
true

julia> f = Fun((x,y) -> x + y);

julia> f(0.1, 0.2) ≈ 0.3
true
```
