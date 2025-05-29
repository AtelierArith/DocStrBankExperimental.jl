```
@evalpoly_derivative(z, c...)
```

Evaluate the polynomial $\sum_k c[k] z^{k-1}$ for the coefficients `c[1]`, `c[2]`, ... and its derivative; that is, the coefficients are given in ascending order by power of `z`.  This macro expands to efficient inline code that uses either Horner's method or, for complex `z`, a more efficient Goertzel-like algorithm.

```jldoctest
julia> @evalpoly(3, 1, 0, 1)
(10, 6)

julia> @evalpoly(2, 1, 0, 1)
(5, 4)

julia> @evalpoly(2, 1, 1, 1)
(7, 5)
```
