sign_chart(f, a, b; atol=1e-4)

Create a sign chart for `f` over `(a,b)`. Returns a collection of named tuples, each with an identified zero or vertical asymptote and the corresponding sign change. The tolerance is used to disambiguate numerically found values.

# Example

```
julia> sign_chart(x -> (x-1/2)/(x*(1-x)), 0, 1)
3-element Vector{NamedTuple{(:zero_oo_NaN, :sign_change)}}:
 (zero_oo_NaN = 0.0, sign_change = an endpoint)
 (zero_oo_NaN = 0.5, sign_change = - to +)
 (zero_oo_NaN = 1.0, sign_change = an endpoint)
```

!!! note "Warning"
    This uses `find_zeros` to find zeros of `f` and `x -> 1/f(x)`. The `find_zeros` function is a hueristic and can miss answers.

