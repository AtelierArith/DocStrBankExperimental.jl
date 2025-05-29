```
disc_log(b::T, x::T) where {T <: FinFieldElem}
```

Return an integer `s` such that $b^s = x$. If no such `x` exists, an exception is thrown.

# Examples

```jldoctest
julia> F = GF(3,4); a = gen(F)^21;

julia> disc_log(gen(F), a)
21
```
