```
exponent(x) -> Int
```

Returns the largest integer `y` such that `2^y ≤ abs(x)`. For a normalized floating-point number `x`, this corresponds to the exponent of `x`.

# Examples

```jldoctest
julia> exponent(8)
3

julia> exponent(64//1)
6

julia> exponent(6.5)
2

julia> exponent(16.0)
4

julia> exponent(3.142e-4)
-12
```
