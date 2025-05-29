```
addmul(a::AbstractLinear, b::AbstractLinear, c)
addmul(a::AbstractLinear, x, c)
```

Add the `c`-fold multiple of the linear combination `b` or of the term `x` to `a`, where `c` is a scalar.

See also [`addmul!`](@ref).
