```
tstbit(x::ZZRingElem, c::Int)
```

Return bit $i$ of x (numbered from 0) as `true` for 1 or `false` for 0.

# Examples

```jldoctest
julia> a = ZZ(12)
12

julia> tstbit(a, 0)
false

julia> tstbit(a, 2)
true
```
