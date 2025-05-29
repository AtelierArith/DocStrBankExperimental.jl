```
clog(x::ZZRingElem, c::ZZRingElem)
clog(x::ZZRingElem, c::Int)
```

Return the ceiling of the logarithm of $x$ to base $c$.

# Examples

```jldoctest
julia> clog(ZZ(12), ZZ(2))
4

julia> clog(ZZ(12), 3)
3

```
