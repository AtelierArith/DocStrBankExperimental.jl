```
taylor_coeff(f, x[, n]; rationalize=true, kwargs...)
```

Calculate the `n`-th order coefficient(s) in the Taylor series of `f` around `x = 0`. If `rationalize`, float coefficients are approximated as rational numbers (this can produce unexpected results for irrational numbers, for example). Keyword arguments `kwargs...` are forwarded to internal `substitute()` calls.

# Examples

```jldoctest
julia> @variables x y
2-element Vector{Num}:
 x
 y

julia> taylor_coeff(series(y, x, 0:5), x, 0:2:4)
3-element Vector{Num}:
 y[0]
 y[2]
 y[4]
```
