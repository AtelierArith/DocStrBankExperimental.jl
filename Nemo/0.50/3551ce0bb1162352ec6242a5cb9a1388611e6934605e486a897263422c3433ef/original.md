```
base(n::ZZRingElem, b::Integer)
```

Return $n$ as a string in base $b$. We require $2 \leq b \leq 62$.

# Examples

```jldoctest
julia> base(ZZ(12), 13)
"c"
```
