```
frexp(val)
```

Return `(x,exp)` such that `x` has a magnitude in the interval $[1/2, 1)$ or 0, and `val` is equal to $x \times 2^{exp}$.

# Examples

```jldoctest
julia> frexp(12.8)
(0.8, 4)
```
