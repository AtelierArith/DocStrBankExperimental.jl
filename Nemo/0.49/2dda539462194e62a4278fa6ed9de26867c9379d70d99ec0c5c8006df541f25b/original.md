```
nbits(x::ZZRingElem)
```

Return the number of binary bits of $x$. We return zero if $x = 0$.

# Examples

```jldoctest
julia> nbits(ZZ(12))
4
```
