```
map_coefficients_to!(output::AbstractPolynomialLike, f::Function, p::AbstractPolynomialLike, nonzero = false)
```

Mutate `output` by replacing each coefficient `α` of `p` by `f(α)`. The function may return zero in which case the term is dropped. If the function is known to never returns zero for a nonzero input, `nonzero` can be set to `true` to get a small speedup. The function returns `output`, which is identically equal to the first argument.

See also [`map_coefficients!`](@ref) and [`map_coefficients`](@ref).
