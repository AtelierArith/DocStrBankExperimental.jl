```
ZZRing <: Ring
ZZRingElem <: RingElem
```

The ring of integers $\mathbb Z$ and its elements. For convenience, we predefine the global variable `const ZZ = ZZRing()`, so we can create elements via [`ZZ(x)`](@ref `(::Ring)(x)`).

# Examples

```jldoctest
julia> ZZ(2)
2

julia> ZZ(2)^100
1267650600228229401496703205376
```
