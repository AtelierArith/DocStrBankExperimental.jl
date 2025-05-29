```
getpaduanum(n)
```

calculates number of Padua points needed to approximate a function using Chebyshev polynomials up to total degree `n`. This number is equal to the number of coefficients. The formula is

$$
N = (n + 1) ⋅ (n + 2) ÷ 2
$$

# Examples

```jldoctest
julia> getpaduanum(13)
105
```
