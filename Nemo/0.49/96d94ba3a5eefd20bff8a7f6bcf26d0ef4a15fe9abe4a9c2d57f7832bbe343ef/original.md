```
flog(x::ZZRingElem, c::ZZRingElem)
flog(x::ZZRingElem, c::Int)
```

Return the floor of the logarithm of $x$ to base $c$.

# Examples

```jldoctest
julia> flog(ZZ(12), ZZ(2))
3

julia> flog(ZZ(12), 3)
2

```
