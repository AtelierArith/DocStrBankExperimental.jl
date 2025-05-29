```
add!(a::AbstractLinear, b::AbstractLinear) -> a
add!(a::AbstractLinear, x) -> a
```

Add the linear combination `b` or the term `x` to `a`. This function modifies `a`.

See also [`addmul!`](@ref), [`sub!`](@ref).
