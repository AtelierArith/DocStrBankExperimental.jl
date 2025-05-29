```
addmul!(a::AbstractLinear, b::AbstractLinear, c) -> a
addmul!(a::AbstractLinear, x, c) -> a
```

Add the `c`-fold multiple of the linear combination `b` or of the term `x` to `a`, where `c` is a scalar. This function modifies `a`.

See also [`addmul`](@ref), [`add!`](@ref), [`sub!`](@ref), [`mul!`](@ref).
