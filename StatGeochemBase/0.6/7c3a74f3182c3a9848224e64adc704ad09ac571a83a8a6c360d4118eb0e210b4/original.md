```julia
nearest(T, x)
```

Convert `x` to the nearest representable value in type T, rounding if inexact

### Examples

```julia julia> nearest(Int, 1234.56) 1235

julia> nearest(Int, Inf) 9223372036854775807

julia> nearest(Int, -Inf) -9223372036854775808 ````
