```
sub!(a::AbstractLinear, b::AbstractLinear) -> a
sub!(a::AbstractLinear, x) -> a
```

Subtract the linear combination `b` or the term `x` from `a`. This function modifies `a`.

See also [`addmul!`](@ref), [`add!`](@ref).
