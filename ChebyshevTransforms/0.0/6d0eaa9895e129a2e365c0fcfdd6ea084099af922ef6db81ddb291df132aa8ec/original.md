```
getdegree(N)
```

calculates total degree, given the number of coefficients or Padua points `N`. Throws an error if `N` is not a possible number of Padua points. The formula is

$$
n = \frac{\sqrt{1 + 8N} - 3}{2}
$$

# Examples

```jldoctest
julia> getdegree(105)
13

julia> getdegree(104)
ERROR: ArgumentError: number of Padua points or coeffs must be (n + 1) * (n + 2) ÷ 2
[...]
```
