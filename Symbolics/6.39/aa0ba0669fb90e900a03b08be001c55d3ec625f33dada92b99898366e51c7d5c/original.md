```
taylor(f, x, [x0=0,] n; rationalize=true, kwargs...)
```

Calculate the `n`-th order term(s) in the Taylor series of `f` around `x = x0`. If `rationalize`, float coefficients are approximated as rational numbers (this can produce unexpected results for irrational numbers, for example). Keyword arguments `kwargs...` are forwarded to internal `substitute()` calls.

# Examples

```jldoctest
julia> @variables x
1-element Vector{Num}:
 x

julia> taylor(exp(x), x, 0:3)
1 + x + (1//2)*(x^2) + (1//6)*(x^3)

julia> taylor(exp(x), x, 0:3; rationalize=false)
1.0 + x + 0.5(x^2) + 0.16666666666666666(x^3)

julia> taylor(√(x), x, 1, 0:3)
1 + (1//2)*(-1 + x) - (1//8)*((-1 + x)^2) + (1//16)*((-1 + x)^3)

julia> isequal(taylor(exp(im*x), x, 0:5), taylor(exp(im*x), x, 0:5))
true
```
