```
(ZZ::ZZRing)(x)
```

Coerce `x` into an element of $\mathbb Z$. Note that `ZZ(x)` is equivalent to [`ZZRingElem(x)`](@ref).

# Examples

```jldoctest
julia> ZZ(2)
2

julia> ZZ(2)^100
1267650600228229401496703205376
```
