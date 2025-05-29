```
combit!(x::ZZRingElem, c::Int)
```

Complement bit $c$ of $x$, where the least significant bit is the $0$-th bit. Note that this function modifies its input in-place.

# Examples

```jldoctest
julia> a = ZZ(12)
12

julia> combit!(a, 2)

julia> a
8
```
