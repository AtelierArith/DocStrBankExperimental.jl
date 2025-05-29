```
coefficients(f::Fun, s::Space) -> Vector
```

Return the coefficients of `f` in the space `s`, which may not be the same as `space(f)`.

# Examples

```jldoctest
julia> f = Fun(x->(3x^2-1)/2);

julia> coefficients(f, Legendre()) ≈ [0, 0, 1]
true
```
