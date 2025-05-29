```
clrbit!(x::ZZRingElem, c::Int)
```

Clear bit $c$ of $x$, where the least significant bit is the $0$-th bit. Note that this function modifies its input in-place.

# Examples

```jldoctest
julia> a = ZZ(12)
12

julia> clrbit!(a, 3)

julia> a
4
```
